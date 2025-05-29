Activate the dev tools, called by `run_server`.

If a parameter can be set by an environment variable, that is listed as:   env: `DASH_****`   Values provided here take precedence over environment variables.

Available dev_tools environment variables:

  * `DASH_DEBUG`
  * `DASH_UI`
  * `DASH_PROPS_CHECK`
  * `DASH_SERVE_DEV_BUNDLES`
  * `DASH_HOT_RELOAD`
  * `DASH_HOT_RELOAD_INTERVAL`
  * `DASH_HOT_RELOAD_WATCH_INTERVAL`
  * `DASH_HOT_RELOAD_MAX_RETRY`
  * `DASH_SILENCE_ROUTES_LOGGING`
  * `DASH_PRUNE_ERRORS`

# Arguments

  * `debug::Bool` - Enable/disable all the dev tools unless overridden by the      arguments or environment variables. Default is $true$ when      $enable_dev_tools$ is called directly, and $false$ when called      via $run_server$. env: $DASH_DEBUG$.
  * `dev_tools_ui::Bool` - Show the dev tools UI. env: $DASH_UI$
  * `dev_tools_props_check::Bool` - Validate the types and values of Dash      component props. env: $DASH_PROPS_CHECK$
  * `dev_tools_serve_dev_bundles::Bool` - Serve the dev bundles. Production   bundles do not necessarily include all the dev tools code.   env: $DASH_SERVE_DEV_BUNDLES$
  * `dev_tools_hot_reload::Bool` - Activate hot reloading when app, assets,   and component files change. env: $DASH_HOT_RELOAD$
  * `dev_tools_hot_reload_interval::Float64` - Interval in seconds for the   client to request the reload hash. Default 3.   env: $DASH_HOT_RELOAD_INTERVAL$
  * `dev_tools_hot_reload_watch_interval::Float64` - Interval in seconds for the   server to check asset and component folders for changes.   Default 0.5. env: $DASH_HOT_RELOAD_WATCH_INTERVAL$
  * `dev_tools_hot_reload_max_retry::Int` - Maximum number of failed reload   hash requests before failing and displaying a pop up. Default 8.   env: $DASH_HOT_RELOAD_MAX_RETRY$
