```
dash(;
        external_stylesheets,
        external_scripts,
        url_base_pathname,
        requests_pathname_prefix,
        routes_pathname_prefix,
        assets_folder,
        assets_url_path,
        assets_ignore,
        serve_locally,
        suppress_callback_exceptions,
        eager_loading ,
        meta_tags,
        index_string,
        assets_external_path,
        include_assets_files,
        show_undo_redo,
        compress,
        update_title
    )
```

Dash is a framework for building analytical web applications. No JavaScript required.

If a parameter can be set by an environment variable, that is listed as:   env: `DASH_****`   Values provided here take precedence over environment variables.

# Arguments

  * `assets_folder::String` - a path, relative to the current working directory,       for extra files to be used in the browser. Default `'assets'`. All .js and .css files will be loaded immediately unless excluded by `assets_ignore`, and other files such as images will be served if requested.
  * `assets_url_path::String` - The local urls for assets will be:       $requests_pathname_prefix * assets_url_path * "/" * asset_path$       where $asset_path$ is the path to a file inside $assets_folder$.       Default ``'assets'`.
  * `assets_ignore::String` - [EXPERIMENTAL] A regex, as a string to pass to $Regex$, for       assets to omit from immediate loading. Ignored files will still be       served if specifically requested. You cannot use this to prevent access       to sensitive files.   :type assets_ignore: string
  * `assets_external_path::String` - [EXPERIMENTAL] an absolute URL from which to load assets.       Use with $serve_locally=false$. Dash can still find js and css to       automatically load if you also keep local copies in your assets       folder that Dash can index, but external serving can improve       performance and reduce load on the Dash server.       env: `DASH_ASSETS_EXTERNAL_PATH`
  * `include_assets_files::Bool` - [EXPERIMENTAL] Default $true$, set to $false$ to prevent       immediate loading of any assets. Assets will still be served if       specifically requested. You cannot use this to prevent access       to sensitive files.       env: `DASH_INCLUDE_ASSETS_FILES`
  * `url_base_pathname::String`: A local URL prefix to use app-wide.       Default $nothing$. Both `requests_pathname_prefix` and       `routes_pathname_prefix` default to `url_base_pathname`.       env: `DASH_URL_BASE_PATHNAME`
  * `requests_pathname_prefix::String`: A local URL prefix for file requests.       Defaults to `url_base_pathname`, and must end with       `routes_pathname_prefix`       env: `DASH_REQUESTS_PATHNAME_PREFIX`
  * `routes_pathname_prefix::String`: A local URL prefix for JSON requests.       Defaults to $url_base_pathname$, and must start and end       with $'/'$.       env: `DASH_ROUTES_PATHNAME_PREFIX`
  * `serve_locally`: [EXPERIMENTAL] If `true` (default), assets and dependencies (Dash and Component js and css) will be served from local URLs. If `false` Dash will use CDN links where available.       (Dash and Component js and css) will be served from local URLs.       If $false$ we will use CDN links where available.
  * `meta_tags::Vector{Dict{String, String}}`: html <meta> tags to be added to the index page.       Each dict should have the attributes and values for one tag, eg:       $Dict("name"=>"description", "content" => "My App")$
  * `index_string::String`: Override the standard Dash index page.       Must contain the correct insertion markers to interpolate various       content into it depending on the app config and components used.       See https://dash.plotly.com/external-resources for details.
  * `external_scripts::Vector`: Additional JS files to load with the page.       Each entry can be a String (the URL) or a Dict{String, String} with $src$ (the URL)       and optionally other $<script>$ tag attributes such as $integrity$       and $crossorigin$.
  * `external_stylesheets::Vector`: Additional CSS files to load with the page.       Each entry can be a String (the URL) or a Dict{String, String} with $href$ (the URL)       and optionally other $<link>$ tag attributes such as $rel$,       $integrity$ and $crossorigin$.
  * `suppress_callback_exceptions::Bool`: Default $false$: check callbacks to       ensure referenced IDs exist and props are valid. Set to $true$       if your layout is dynamic, to bypass these checks.       env: `DASH_SUPPRESS_CALLBACK_EXCEPTIONS`
  * `prevent_initial_callbacks::Bool`: Default $false$: Sets the default value       of $prevent_initial_call$ for all callbacks added to the app.       Normally all callbacks are fired when the associated outputs are first       added to the page. You can disable this for individual callbacks by       setting $prevent_initial_call$ in their definitions, or set it       $true$ here in which case you must explicitly set it $false$ for       those callbacks you wish to have an initial call. This setting has no       effect on triggering callbacks when their inputs change later on.
  * `show_undo_redo::Bool`: Default $false$, set to $true$ to enable undo       and redo buttons for stepping through the history of the app state.
  * `compress::Bool`: Default $true$, controls whether gzip is used to compress       files and data served by HTTP.jl when supported by the client. Set to       $false$ to disable compression completely.
  * `update_title::String`: Default $Updating...$. Configures the document.title       (the text that appears in a browser tab) text when a callback is being run.       Set to '' if you don't want the document.title to change or if you       want to control the document.title through a separate component or       clientside callback.
