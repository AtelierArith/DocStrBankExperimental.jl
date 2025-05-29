```
GitHubActions(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/github/workflows/CI.yml",
    destination="CI.yml",
    linux=true,
    osx=false,
    windows=false,
    x64=true,
    x86=false,
    coverage=true,
    extra_versions=["1.6", "1.11", "pre"],
)
```

Integrates your packages with [GitHub Actions](https://github.com/features/actions).

## Keyword Arguments

  * `file::AbstractString`: Template file for the workflow file.
  * `destination::AbstractString`: Destination of the workflow file, relative to `.github/workflows`.
  * `linux::Bool`: Whether or not to run builds on Linux.
  * `osx::Bool`: Whether or not to run builds on OSX (MacOS).
  * `windows::Bool`: Whether or not to run builds on Windows.
  * `x64::Bool`: Whether or not to run builds on 64-bit architecture.
  * `x86::Bool`: Whether or not to run builds on 32-bit architecture.
  * `coverage::Bool`: Whether or not to publish code coverage. Another code coverage plugin such as [`Codecov`](@ref) must also be included.
  * `extra_versions::Vector`: Extra Julia versions to test, as strings or `VersionNumber`s.

!!! note
    If using coverage plugins, don't forget to manually add your API tokens as secrets, as described [here](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/creating-and-using-encrypted-secrets#creating-encrypted-secrets).

