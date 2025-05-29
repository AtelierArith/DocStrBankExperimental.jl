```
create_params(
    defn_path::AbstractString,
    param_paths...;
    error_on_unused::Bool = false,
    out_path::AbstractString = "",
)
```

Entry function - given the path to the parameter definitions and files, parse and create a params dictionary.

The defn*path and param*paths can be either a single yaml file, or a directory containing yaml files.

# Arguments

  * `defn_path`: path to the parameter definitions
  * `param_paths...`: paths to parameter files or directories. The files will be merged in the passed order so that item 'a' in the first params will be overwritten by item 'a' in the second params.
  * `out_path`: path to directory where computed params will be saved if passed
  * `error_on_unused`: throw a hard error if there are unused parameters, otherwise warnings are only printed

# Returns

  * dictionary with computed/validated model paramters with defaults filled in where needed
