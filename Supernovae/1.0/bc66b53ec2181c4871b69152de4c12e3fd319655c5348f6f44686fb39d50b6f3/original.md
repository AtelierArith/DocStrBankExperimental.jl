```
main(toml_path::AbstractString, verbose::Bool, profile::Bool)
```

Loads `toml_path`, and sets up logging with verbosity based on `verbose`. Runs [`run_Supernovae`](@ref) and if `profile` is `true`, also profiles the code.

# Arguments

  * `toml_path::AbstractString`: Path to toml input file.
  * `verbose::Bool`: Set verbosity of logging
  * `profile::Bool`: If true, profile [`run_Supernovae`](@ref)
