```
function add_artifact!(
    artifacts_toml::String, name::String, tarball_url::String;
    clear=true,
    platform::Union{Platform,Nothing}=nothing,
    lazy::Bool=false,
    force::Bool=false
)
```

Downloads tarball from `tarball_url`, extracts it and adds it as an artifact with name `name` to the file `artifacts_toml`. If `clear` is true, the artifact itself is deleted afterwards. The rest of the keyword arguments are passed to `Pkg.Artifacts.bind_artifact!`.

From [its docstring](https://julialang.github.io/Pkg.jl/dev/api/#Pkg.Artifacts.bind_artifact!):

> If `platform` is not `nothing`, this artifact is marked as platform-specific, and will be a multi-mapping.  It is valid to bind multiple artifacts with the same name, but different `platform`s and `hash`'es within the same `artifacts_toml`.  If `force` is set to `true`, this will overwrite a pre-existant mapping, otherwise an error is raised.
>
> [...] If `lazy` is set to `true`, even if download information is available, this artifact will not be downloaded until it is accessed via the `artifact"name"` syntax, or `ensure_artifact_installed()` is called upon it.

