```
compile_traces(mod::Module, trace_files::AbstractString...; verbose=false, progress=true, warn=false, inline=false)
compile_traces(mod::Module, trace_files::AbstractVector{<:AbstractString}; verbose=false, progress=true, warn=false, inline=false)
```

Execute a set of precompile statements from one or more trace files, returning a `CompilationMetrics` result.

Trace file paths will be roughly OS-normalized, substituting '/' with '\' on Windows.

`verbose = false` implies `progress = false`. Turn off `progress = false` when `\r` is not well supported, i.e. in CI.

`warn = true` will emit a warning upon failure to precompile a given statement.

Certain options may be overriden by environment variables. These variables are of the form `JULIA_COMPILE_TRACES_<OPTION>`, and operate similarly to `JULIA_DEBUG`: the value of these variables is a coma-separated list of modules, and the corresponding option will be enabled for any module appearing in the list. Available options are:

  * `JULIA_COMPILE_TRACES_VERBOSE`: set value of the `verbose` boolean parameter to `true` for specified modules.
  * `JULIA_COMPILE_TRACES_WARN`: set value of the `warn` boolean parameter to `true` for specified modules.

For example, `JULIA_COMPILE_TRACES_WARN=PackageA,PackageB` will forcefully set the parameter `warn` to `true` when called with a `mod::Module` argument whose name is eitehr `PackageA` or `PackageB`.

If `inline` is set to true, the `precompile(...)` directives will be executed in `mod`; otherwise, a new module is created inside `mod`, with a special namespace which allows referring to any module loaded in the Julia session. Which value to use for `inline` will depend on the format of trace files, which may be in one of two formats depending on how they were generated:

  * Trace files generated by the command-line option `--trace-file=<file>`: they require the use of `inline = false`. All functions and most types are prefixed with their defining module, e.g. `Base.collect`, `Base.getindex`, etc. regardless of the scope in which code was evaluated.
  * Trace files generated by [SnoopCompile.jl](https://github.com/timholy/SnoopCompile.jl) using `SnoopCompile.parcel` and later `SnoopCompile.write`: they require the use of `inline = true`. All functions and types are assumed to be in the scope of the package for which traces were generated.

The difference between the two formats is the scope assumed to be used when later executing the precompile directives. All trace files *must be in the same format*, but you can make two calls to `compile_traces` where each uses trace files of a different format.

!!! warning
    If the traces are meant to be compiled during package precompilation, then `mod` **must** be the module being precompiled (i.e. `@__MODULE__`). Otherwise, you will get the unfamous error:

    > ERROR: LoadError: Evaluation into the closed module <mod> breaks incremental compilation because the side effects will not be permanent. This is likely due to some other module mutating <mod> with `eval` during precompilation - don't do this.


Only the statements which are bound to known modules and types will be compiled. However, when using precompile statements from `--trace-file=<file>`, it is sufficient that top-level packages or modules are loaded in the session; if package A uses a type for B, B will already have been loaded with A, and so will be known to the session.

If generating a trace file from a script which includes types and functions defined in `Main`, it may be good practice to filter out traces which contain `Main.`. Otherwise warnings will be raised, unless you really are compiling functions and types that are defined in the running session.
