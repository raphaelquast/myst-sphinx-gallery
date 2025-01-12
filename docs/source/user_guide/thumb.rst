.. _thumbnail_strategy:

====================
Thumbnail Strategies
====================

Overview
--------

- **one image** - If there only one image in an example file, no additional configuration is needed, and that image will be used as the gallery thumbnail.

- **multiple images** - If there are multiple figures in an example file, you can specify the strategy to determine which thumbnail will be used for the gallery. The following strategies are supported:

  1. **alt** - If the alt attribute of an image/figure is set to gallery_thumbnail, that image/figure will be used as the gallery thumbnail for this file.
  2. **first/last** - If there are multiple images that can be used as the gallery thumbnail, the first/last image will be selected. You can specify the strategy by setting the thumbnail_strategy in the configuration file. The default value is first.
  3. **code/markdown** - For Jupyter notebook files, both markdown and code cells can contain images. You can specify the strategy by setting the notebook_thumbnail_strategy in the configuration file. The default value is code.

- **no image** - If no image/figure is found, the default thumbnail will be used.


``alt`` attribute
-----------------

You can specify that an image/figure will be used as the gallery thumbnail for this file by setting the ``alt`` attribute to ``gallery_thumbnail``. The following syntaxes are supported:

ReStructuredText files
~~~~~~~~~~~~~~~~~~~~~~

1. image directive

.. code-block:: rst
   :emphasize-lines: 2

   .. image:: path/to/image.png
      :alt: gallery_thumbnail


2. figure directive

.. code-block:: rst
   :emphasize-lines: 2

   .. figure:: path/to/image.png
      :alt: gallery_thumbnail



Markdown or notebook files
~~~~~~~~~~~~~~~~~~~~~~~~~~

Since ``myst-nb`` supports both markdown and notebook files, the syntax for markdown or notebook files is the same. You can use either the conventional markdown image syntax or the MyST image/figure directive.

.. seealso::

   - MyST Markdown: `myst-parser <https://myst-parser.readthedocs.io/en/latest/>`_
   - MyST Notebook: `myst-nb <https://myst-nb.readthedocs.io/en/latest/>`_


1. Conventional markdown image syntax

   .. code-block:: markdown

      ![gallery_thumbnail](path/to/image.png)

2. MyST Images directive

   .. code-block:: markdown
      :emphasize-lines: 2

      ```{image} path/to/image.png
         :alt: gallery_thumbnail
      ```

3. MyST Figure directive

   .. code-block:: markdown
      :emphasize-lines: 2

      ```{figure} path/to/image.png
         :alt: gallery_thumbnail
      ```

``first/last`` strategy
-----------------------

There may be multiple images are candidates for the gallery thumbnail for an example file. For example, if ``alt`` attribute is not set, there are multiple images can be used as the gallery thumbnail. If you want to use the ``first/last`` image as the gallery thumbnail, you can specify the strategy in the configuration file. The default value is ``first``.

If you want to use the last image as the gallery thumbnail, you can add the following configuration to the ``conf.py`` file:

.. code-block:: python
   :caption: conf.py

   myst_sphinx_gallery_config = GalleryConfig(
      ...,
      thumbnail_strategy = "last",
      )

.. _code_markdown:

``code/markdown`` strategy
--------------------------

For Jupyter notebook files, both ``markdown`` and ``code`` cells can contain images. You can specify the which cell type will be detected first as the gallery thumbnail by setting the ``notebook_thumbnail_strategy`` in the configuration file. The default value is ``code``.

For example, if you want to use the ``markdown`` cell as the gallery thumbnail, you can add the following configuration to the ``conf.py`` file:

.. code-block:: python
   :caption: conf.py

   myst_sphinx_gallery_config = GalleryConfig(
      ...,
      notebook_thumbnail_strategy = "markdown",
      )

default thumbnail
-----------------

If no image/figure is found, the default thumbnail will be used. You can specify the default thumbnail by setting the ``default_thumbnail_file`` in the configuration file.

.. note::

   The default value is None, which means a default thumbnail provided by this extension will be used (This figure is directly copied from the ``Sphinx Gallery`` extension).

For example, if you want to use the ``_static/thumbnail.png``, which is your custom image, as the default thumbnail, you can add the following configuration to the ``conf.py`` file:

.. code-block:: python
   :caption: conf.py

   myst_sphinx_gallery_config = GalleryConfig(
      ...,
      default_thumbnail_file = "_static/thumbnail.png",
      )
