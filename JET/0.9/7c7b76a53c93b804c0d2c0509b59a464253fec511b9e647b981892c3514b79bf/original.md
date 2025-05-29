```
report_file(file::AbstractString; jetconfigs...) -> JETToplevelResult
```

Analyzes `file` to find type-level errors and returns back detected problems.

This function looks for `.JET.toml` configuration file in the directory of `file`, and searches *upward* in the file tree until a `.JET.toml` is (or isn't) found. When found, the configurations specified in the file are applied. See [JET's configuration file specification](@ref config-file) for more details.

The [general configurations](@ref) and [the error analysis specific configurations](@ref jetanalysis-config) can be specified as a keyword argument, and if given, they are preferred over the configurations specified by a `.JET.toml` configuration file.

!!! tip
    When you want to analyze your package but no files that actually use its functions are available, [the `analyze_from_definitions` option](@ref toplevel-config) may be useful since it allows JET to analyze methods based on their declared signatures. For example, JET can analyze JET itself in this way:

    ```julia-repl
    # from the root directory of JET.jl
    julia> report_file("src/JET.jl";
                       analyze_from_definitions = true)
    ```

    See also [`report_package`](@ref).


!!! note
    This function enables the `toplevel_logger` configuration with the default logging level by default. You can still explicitly specify and configure it:

    ```julia
    report_file(args...;
                toplevel_logger = nothing, # suppress the toplevel logger
                jetconfigs...) # other configurations
    ```

    See [JET's top-level analysis configurations](@ref toplevel-config) for more details.

