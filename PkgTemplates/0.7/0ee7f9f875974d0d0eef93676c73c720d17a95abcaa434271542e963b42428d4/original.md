```
TagBot(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/github/workflows/TagBot.yml",
    destination="TagBot.yml",
    trigger="JuliaTagBot",
    token=Secret("GITHUB_TOKEN"),
    ssh=Secret("DOCUMENTER_KEY"),
    ssh_password=nothing,
    changelog=nothing,
    changelog_ignore=nothing,
    gpg=nothing,
    gpg_password=nothing,
    registry=nothing,
    branches=nothing,
    dispatch=nothing,
    dispatch_delay=nothing,
)
```

Adds GitHub release support via [TagBot](https://github.com/JuliaRegistries/TagBot).

## Keyword Arguments

  * `file::AbstractString`: Template file for the workflow file.
  * `destination::AbstractString`: Destination of the workflow file, relative to `.github/workflows`.
  * `trigger::AbstractString`: Username of the trigger user for custom registries.
  * `token::Secret`: Name of the token secret to use.
  * `ssh::Secret`: Name of the SSH private key secret to use.
  * `ssh_password::Secret`: Name of the SSH key password secret to use.
  * `changelog::AbstractString`: Custom changelog template.
  * `changelog_ignore::Vector{<:AbstractString}`: Issue/pull request labels to ignore in the changelog.
  * `gpg::Secret`: Name of the GPG private key secret to use.
  * `gpg_password::Secret`: Name of the GPG private key password secret to use.
  * `registry::AbstractString`: Custom registry, in the format `owner/repo`.
  * `branches::Bool`: Whether or not to enable the `branches` option.
  * `dispatch::Bool`: Whether or not to enable the `dispatch` option.
  * `dispatch_delay::Int`: Number of minutes to delay for dispatch events.
