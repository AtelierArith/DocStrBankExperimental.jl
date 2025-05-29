```
Git(;
    ignore=String[],
    name=nothing,
    email=nothing,
    branch=LibGit2.getconfig("init.defaultBranch", "main")
    ssh=false,
    jl=true,
    manifest=false,
    gpgsign=false,
)
```

Creates a Git repository and a `.gitignore` file.

## Keyword Arguments

  * `ignore::Vector{<:AbstractString}`: Patterns to add to the `.gitignore`. See also: [`gitignore`](@ref).
  * `name::AbstractString`: Your real name, if you have not set `user.name` with Git.
  * `email::AbstractString`: Your email address, if you have not set `user.email` with Git.
  * `branch::AbstractString`: The desired name of the repository's default branch.
  * `ssh::Bool`: Whether or not to use SSH for the remote. If left unset, HTTPS is used.
  * `jl::Bool`: Whether or not to add a `.jl` suffix to the remote URL.
  * `manifest::Bool`: Whether or not to commit `Manifest.toml`.
  * `gpgsign::Bool`: Whether or not to sign commits with your GPG key. This option requires that the Git CLI is installed, and for you to have a GPG key associated with your committer identity.
