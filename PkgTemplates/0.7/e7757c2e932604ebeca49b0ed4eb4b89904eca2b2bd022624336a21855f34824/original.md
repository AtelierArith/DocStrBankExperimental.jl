```
CirrusCI(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/cirrus.yml",
    image="freebsd-12-0-release-amd64",
    coverage=true,
    extra_versions=["1.6", "1.11", "nightly"],
)
```

Integrates your packages with [Cirrus CI](https://cirrus-ci.org) via [CirrusCI.jl](https://github.com/ararslan/CirrusCI.jl).

## Keyword Arguments

  * `file::AbstractString`: Template file for `.cirrus.yml`.
  * `image::AbstractString`: The FreeBSD image to be used.
  * `coverage::Bool`: Whether or not to publish code coverage. [`Codecov`](@ref) must also be included.
  * `extra_versions::Vector`: Extra Julia versions to test, as strings or `VersionNumber`s.

!!! note
    Code coverage submission from Cirrus CI is not yet supported by [Coverage.jl](https://github.com/JuliaCI/Coverage.jl).

