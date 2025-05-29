```
Documenter{T}(;
    make_jl="~/.julia/packages/PkgTemplates/MepaC/templates/docs/make.jlt",
    index_md="~/.julia/packages/PkgTemplates/MepaC/templates/docs/src/index.md",
    assets=String[],
    logo=Logo(),
    canonical_url=make_canonical(T),
    devbranch=nothing,
    edit_link=:devbranch,
    makedocs_kwargs=Dict{Symbol,Any}(),
)
```

Sets up documentation generation via [Documenter.jl](https://github.com/JuliaDocs/Documenter.jl). Documentation deployment depends on `T`, where `T` is some supported CI plugin, or `Nothing` to only support local documentation builds.

!!! note
    If you are deploying documentation with GitHub Actions or Travis CI, don't forget to complete [the required configuration](https://documenter.juliadocs.org/stable/man/hosting/#Hosting-Documentation). In particular, you may need to run

    ```julia
    using DocumenterTools; DocumenterTools.genkeys(user="MyUser", repo="MyPackage.jl")
    ```

    and follow the instructions there.


## Supported Type Parameters

  * `GitHubActions`: Deploys documentation to [GitHub Pages](https://pages.github.com) with the help of [`GitHubActions`](@ref).
  * `TravisCI`: Deploys documentation to [GitHub Pages](https://pages.github.com) with the help of [`TravisCI`](@ref).
  * `GitLabCI`: Deploys documentation to [GitLab Pages](https://pages.gitlab.com) with the help of [`GitLabCI`](@ref).
  * `NoDeploy` (default): Does not set up documentation deployment.

## Keyword Arguments

  * `make_jl::AbstractString`: Template file for `make.jl`.
  * `index_md::AbstractString`: Template file for `index.md`.
  * `assets::Vector{<:AbstractString}`: Extra assets for the generated site.
  * `logo::Logo`: A [`Logo`](@ref) containing documentation logo information.
  * `canonical_url::Union{Function, Nothing}`: A function to generate the site's canonical URL. The default value will compute GitHub Pages and GitLab Pages URLs for [`TravisCI`](@ref) and [`GitLabCI`](@ref), respectively. If set to `nothing`, no canonical URL is set.
  * `edit_link::Union{AbstractString, Symbol, Nothing}`: Branch, tag or commit that the "Edit on…" link will point to. Defaults to the branch identified by `devbranch`. If `edit_link=:commit`, then the link will point to the latest commit when docs are built. If `edit_link=nothing`, then the "Edit on…" link will be hidden altogether.
  * `devbranch::Union{AbstractString, Nothing}`: Branch that will trigger docs deployment. If `nothing`, then the default branch according to the `Template` will be used.
  * `makedocs_kwargs::Dict{Symbol,Any}`: Extra keyword arguments to be inserted into `makedocs`.
