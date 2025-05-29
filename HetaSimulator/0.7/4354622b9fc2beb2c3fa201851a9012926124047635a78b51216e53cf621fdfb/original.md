```
heta_build(
  target_dir::AbstractString;
  declaration::String = "platform",
  units_check::Bool = false,
  log_mode::String = "error",
  log_path::String = "build.log",
  log_level::String = "info",
  debug::Bool = false,
  dist_dir::String = "dist",
  meta_dir::String = "meta",
  source::String = "index.heta",
  type::String = "heta",
  export_::Union{String, Nothing} = nothing,
)
```

Builds the models from Heta-based platform

See `heta compiler` docs for details: [https://hetalang.github.io/#/heta-compiler/cli-references?id=running-build-with-cli-options](https://hetalang.github.io/#/heta-compiler/cli-references?id=running-build-with-cli-options)

Arguments:

  * `target_dir` : path to a Heta platform directory
  * `declaration` : path to declaration file. Default is `"platform"`
  * `units_check` : if set to `true` units will be checked for the consistancy
  * `log_mode` : log mode. Default is `"error"`
  * `log_path` : path to the log file. Default is `"build.log"`
  * `log_level` : log level to display. Default is `"info"`
  * `debug` : turn on debug mode. Default is `false`
  * `dist_dir` : directory path, where to write distributives to. Default is `"dist"`
  * `meta_dir` : meta directory path. Default is `"meta"`
  * `source` : path to the main heta module. Default is `"index.heta"`
  * `type` : type of the source file. Default is `"heta"`
  * `export_` : export the model to the specified format: `Julia,JSON`, `{format:SBML,version:L3V1},JSON`
