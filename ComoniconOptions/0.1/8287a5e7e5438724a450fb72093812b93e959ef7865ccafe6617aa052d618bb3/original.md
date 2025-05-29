```
read_options(comonicon; kwargs...)
```

Read in Comonicon build options. The argument `comonicon` can be:

  * a module of a Comonicon CLI project.
  * a path to a Comonicon CLI project that contains either `JuliaComonicon.toml` or `Comonicon.toml`.
  * a path to a Comonicon CLI build configuration file named either `JuliaComonicon.toml` or `Comonicon.toml`.

In some cases, you might want to change the configuration written in the TOML file temporarily, e.g for writing build tests etc. In this case, you can modify the configuration using corresponding keyword arguments.

keyword arguments of [`Application`](@ref) and [`SysImg`](@ref) are the same, thus keys like `filter_stdlibs` are considered ambiguous in `read_options`, but you can specifiy them by specifiy the specific [`Application`](@ref) or [`SysImg`](@ref) object, e.g

```julia
read_options(MyCLI; sysimg=SysImg(filter_stdlibs=false))
```

See also [`Comonicon`](@ref), [`Install`](@ref), [`SysImg`](@ref), [`Application`](@ref), [`Download`](@ref), [`Precompile`](@ref).
