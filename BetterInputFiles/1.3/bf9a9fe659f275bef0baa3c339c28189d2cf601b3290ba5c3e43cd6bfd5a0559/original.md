```
setup_input(input_path::AbstractString, verbose::Bool, ext::InputExt; paths::OrderedDict{String, Tuple{String, String}}=OrderedDict{String, Tuple{String, String}}(), log_path::String="output_path", custom_metadata::Vector{Tuple{String, String}}=Vector{Tuple{String, String}}())
```

Main `BetterInputFiles` function, given a path to an input file, this will preprocess, load, and postprocess the input file, including setting up paths and logging.

# Arguments

  * `input_path::AbstractString`: Path to input file
  * `verbose::Bool`: Whether to log `@debug` messages
  * `ext::InputExt`: Extension specifier
  * `paths::OrderedDict{String, Tuple{String, String}}=OrderedDict{String, Tuple{String, String}}`: Paths to expand. `paths` will be merged with [`SetupModule.default_paths`](@ref), with `paths` taking preference. See [`SetupModule.default_paths`](@ref) for the syntax of `paths`
  * `log_path::String="output_path"`: The `"path_name"` of the directory where logging should output. `log_path` must exist in `paths` or, be defined by [`SetupModule.default_paths`](@ref)
  * `custom_metadata::Vector{Tuple{String, String}}=Vector{Tuple{String, String}}()`: Additonal metadata to include in the input file, in addition to creation date and `input_path`
