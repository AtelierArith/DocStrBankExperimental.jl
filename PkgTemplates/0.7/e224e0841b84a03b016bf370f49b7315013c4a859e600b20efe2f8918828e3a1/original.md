```
TravisCI(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/travis.yml",
    linux=true,
    osx=false,
    windows=false,
    x64=true,
    x86=false,
    arm64=false,
    coverage=true,
    extra_versions=["1.6", "1.11", "nightly"],
)
```

Integrates your packages with [Travis CI](https://travis-ci.com).

## Keyword Arguments

  * `file::AbstractString`: Template file for `.travis.yml`.
  * `linux::Bool`: Whether or not to run builds on Linux.
  * `osx::Bool`: Whether or not to run builds on OSX (MacOS).
  * `windows::Bool`: Whether or not to run builds on Windows.
  * `x64::Bool`: Whether or not to run builds on 64-bit architecture.
  * `x86::Bool`: Whether or not to run builds on 32-bit architecture.
  * `arm64::Bool`: Whether or not to run builds on the ARM64 architecture.
  * `coverage::Bool`: Whether or not to publish code coverage. Another code coverage plugin such as [`Codecov`](@ref) must also be included.
  * `extra_versions::Vector`: Extra Julia versions to test, as strings or `VersionNumber`s.
