```
DroneCI(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/drone.star",
    amd64=true,
    arm=false,
    arm64=false,
    extra_versions=["1.6", "1.11"],
)
```

Integrates your packages with [Drone CI](https://drone.io).

## Keyword Arguments

  * `file::AbstractString`: Template file for `.drone.star`.
  * `destination::AbstractString`: File destination, relative to the repository root. For example, you might want to generate a `.drone.yml` instead of the default Starlark file.
  * `amd64::Bool`: Whether or not to run builds on AMD64.
  * `arm::Bool`: Whether or not to run builds on ARM (32-bit).
  * `arm64::Bool`: Whether or not to run builds on ARM64.
  * `extra_versions::Vector`: Extra Julia versions to test, as strings or `VersionNumber`s.

!!! note
    Nightly Julia is not supported.

