```
export_directory(start_dir::String="."; kwargs...)
```

Search recursively for all Pluto notebooks in the current folder, and for each notebook:

  * Run the notebook and wait for all cells to finish
  * Export the state object
  * Create a .html file with the same name as the notebook, which has:

      * The JS and CSS assets to load the Pluto editor
      * The state object embedded
      * Extra functionality enabled, such as hidden UI, binder button, and a live bind server

# Keyword rguments

  * `Export_enabled::Bool = true`: Generate static HTML files? This setting can only be `false` if you are also running a slider server.
  * `Export_output_dir::Union{Nothing, String} = nothing`: Folder to write generated HTML files to (will create directories to preserve the input folder structure). The behaviour of the default value depends on whether you are running the slider server, or just exporting. If running the slider server, we use a temporary directory; otherwise, we use `start_dir` (i.e. we generate each HTML file in the same folder as the notebook file).
  * `Export_exclude::Vector{String} = String[]`: List of notebook files to skip. Provide paths relative to `start_dir`.  You can use the `*` wildcard and other [glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)).
  * `Export_ignore_cache::Vector = String[]`: List of notebook files that should always re-run, skipping the `cache_dir` system. Provide paths relative to `start_dir`.  You can use the `*` wildcard and other [glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)).
  * `Export_cache_dir::Union{Nothing, String} = nothing`: If provided, use this directory to read and write cached notebook states. Caches will be indexed by the hash of the notebook file, but you need to take care to invalidate the cache when Pluto or this export script updates. Useful in combination with https://github.com/actions/cache, see https://github.com/JuliaPluto/static-export-template for an example.
  * `Export_baked_state::Bool = true`: base64-encode the state object and write it inside the .html file. If `false`, a separate `.plutostate` file is generated. A separate statefile allows us to show a loading bar in pluto while the statefile is loading, but it can complicate setup in some environments.
  * `Export_baked_notebookfile::Bool = true`: base64-encode the .jl notebook source and write it inside the .html file. If `false`, a separate `.jl` file is generated (or the original is used). The main difference is in the "Edit or run this notebook > On your computer" flow on the HTML file: with a separate notebook file (default), it will be a URL that you can copy and open with Pluto. With a baked notebook file, it will be a download button, and visitors need to save the notebook on their local drive, which can be more complicated.
  * `Export_disable_ui::Bool = true`: Hide all buttons and toolbars in Pluto to make it look like an article.
  * `Export_offer_binder::Bool = true`: Show a "Run on Binder" button on the notebooks.
  * `Export_binder_url::Union{Nothing, String} = nothing`: ADVANCED: URL of the binder repository to load when you click the "Run on binder" button in the top right, this will be set automatically if you leave it at the default value. This setting is quite advanced, and only makes sense if you have a fork of `https://github.com/fonsp/pluto-on-binder/` (because you want to control the binder launch, or because you are using your own fork of Pluto). If so, the setting should be of the form `"https://mybinder.org/v2/gh/fonsp/pluto-on-binder/v0.17.2"`, where `fonsp/pluto-on-binder` is the name of your repository, and `v0.17.2` is a tag or commit hash.
  * `Export_slider_server_url::Union{Nothing, String} = nothing`: If 1) you are using this setup to export HTML files for notebooks, AND 2) you are running the slider server **on another setup/computer**, then this setting should be the URL pointing to the slider server, e.g. `"https://sliderserver.mycoolproject.org/"`. For example, you need this if you use GitHub Actions and GitHub Pages to generate HTML files, with a slider server on DigitalOcean. === If you only have *one* server for both the static exports and the slider server, and people will read notebooks directly on your server, then the default value `nothing` will work: it will automatically make the HTML files use their current domain for the slider server.
  * `Export_create_index::Bool = true`: Automatically generate an `index.html` file, listing all the exported notebooks (only if no `index.jl` or `index.html` file exists already).
  * `Export_create_pluto_featured_index::Union{Nothing, Bool} = nothing`: Use the Pluto Featured GUI to display the notebooks on the auto-generated index page, using frontmatter for title, description, image, and more. The default is currently `false`, but it might change in the future. Set to `true` or `false` explicitly to fix a value.
  * `notebook_paths::Vector{String}=find_notebook_files_recursive(start_dir)`: If you do not want the recursive save behaviour, then you can set this to a vector of absolute paths. In that case, `start_dir` is ignored, and you should set `Export_output_dir`.
