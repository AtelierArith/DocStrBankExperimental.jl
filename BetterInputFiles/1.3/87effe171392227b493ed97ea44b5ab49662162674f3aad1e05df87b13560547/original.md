```
setup_input(input_path::AbstractString, verbose::Bool; paths::OrderedDict{String, Tuple{String, String}}=OrderedDict{String, Tuple{String, String}}(), log_path::String="output_path", custom_metadata::Vector{Tuple{String, String}}=Vector{Tuple{String, String}}())
```

Automatically choose input file extension, then run [`setup_input(::AbstractString, ::Bool, ::InputExt, ::OrderedDict{String, Tuple{String, String}}, ::String, ::Vector{Tuple{String, String}})`](@ref)

# Arguments

  * `input_path::AbstractString`: Path to input file
  * `verbose::Bool`: Whether to log `@debug` messages
  * `paths::OrderedDict{String, Tuple{String, String}}=OrderedDict{String, Tuple{String, String}}`: Paths to expand. `paths` will be merged with [`SetupModule.default_paths`](@ref), with `paths` taking preference. See [`SetupModule.default_paths`](@ref) for the syntax of `paths`
  * `log_path::String="output_path"`: The `"path_name"` of the directory where logging should output. `log_path` must exist in `paths` or, be defined by [`SetupModule.default_paths`](@ref)
  * `custom_metadata::Vector{Tuple{String, String}}=Vector{Tuple{String, String}}()`: Additonal metadata to include in the input file, in addition to creation date and `input_path`
