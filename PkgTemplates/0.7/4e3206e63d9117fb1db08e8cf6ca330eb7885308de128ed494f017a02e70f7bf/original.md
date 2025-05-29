```
Tests(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/test/runtests.jlt",
    project=false,
    aqua=false,
    aqua_kwargs=NamedTuple(),
    jet=false,
)
```

Sets up testing for packages.

## Keyword Arguments

  * `file::AbstractString`: Template file for `runtests.jl`.
  * `project::Bool`: Whether or not to create a new project for tests (`test/Project.toml`). See [the Pkg docs](https://julialang.github.io/Pkg.jl/v1/creating-packages/#Test-specific-dependencies-in-Julia-1.2-and-above-1) for more details.
  * `aqua::Bool`: Controls whether or not to add quality tests with [Aqua.jl](https://github.com/JuliaTesting/Aqua.jl).
  * `aqua_kwargs::NamedTuple`: Which keyword arguments to supply to Aqua tests (many people use `ambiguities=false` for example)
  * `jet::Bool`: Controls whether or not to add a linting test with [JET.jl](https://github.com/aviatesk/JET.jl) (works best on type-stable code)

!!! note
    Managing test dependencies with `test/Project.toml` is only supported in Julia 1.2 and later.

