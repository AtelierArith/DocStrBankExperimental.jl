```
AppVeyor(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/appveyor.yml",
    x86=false,
    coverage=true,
    extra_versions=["1.6", "1.11", "nightly"],
)
```

Integrates your packages with [AppVeyor](https://appveyor.com) via [AppVeyor.jl](https://github.com/JuliaCI/Appveyor.jl).

## Keyword Arguments

  * `file::AbstractString`: Template file for `.appveyor.yml`.
  * `x86::Bool`: Whether or not to run builds on 32-bit systems, in addition to the default 64-bit builds.
  * `coverage::Bool`: Whether or not to publish code coverage. [`Codecov`](@ref) must also be included.
  * `extra_versions::Vector`: Extra Julia versions to test, as strings or `VersionNumber`s.
