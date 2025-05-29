```
Template(; kwargs...)
```

A configuration used to generate packages.

## Keyword Arguments

### User Options

  * `user::AbstractString=""`: GitHub (or other code hosting service) username. The default value comes from the global Git config (`github.user`). If no value is obtained, many plugins that use this value will not work.
  * `authors::Union{AbstractString, Vector{<:AbstractString}}="terasakisatoshi <terasakisatoshi.math@gmail.com> and contributors"`: Package authors. Like `user`, it takes its default value from the global Git config (`user.name` and `user.email`).

### Package Options

  * `dir::AbstractString="~/.julia/dev"`: Directory to place packages in.
  * `host::AbstractString="github.com"`: URL to the code hosting service where packages will reside.
  * `julia::VersionNumber=v"1.6.7"`: Minimum allowed Julia version.

### Template Plugins

  * `plugins::Vector{<:Plugin}=Plugin[]`: A list of [`Plugin`](@ref)s used by the template. The default plugins are [`ProjectFile`](@ref), [`SrcDir`](@ref), [`Tests`](@ref), [`Readme`](@ref), [`License`](@ref), [`Git`](@ref), [`CompatHelper`](@ref), [`TagBot`](@ref) and [`GitHubActions`](@ref). To disable a default plugin, pass in the negated type: `!PluginType`. To override a default plugin instead of disabling it, pass in your own instance.

### Interactive Mode

  * `interactive::Bool=false`: In addition to specifying the template options with keywords, you can also build up a template by following a set of prompts. To create a template interactively, set this keyword to `true`. See also the similar [`generate`](@ref) function.

---

To create a package from a `Template`, use the following syntax:

```julia
julia> t = Template();

julia> t("PkgName")
```
