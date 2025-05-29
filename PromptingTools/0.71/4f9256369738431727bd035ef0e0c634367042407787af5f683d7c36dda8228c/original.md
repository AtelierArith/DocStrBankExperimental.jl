```
load_templates!(dir_templates::Union{String, Nothing} = nothing;
    remember_path::Bool = true,
    remove_templates::Bool = isnothing(dir_templates),
    store::Dict{Symbol, <:Any} = TEMPLATE_STORE,
    metadata_store::Vector{<:AITemplateMetadata} = TEMPLATE_METADATA)
```

Loads templates from folder `templates/` in the package root and stores them in `TEMPLATE_STORE` and `TEMPLATE_METADATA`.

Note: Automatically removes any existing templates and metadata from `TEMPLATE_STORE` and `TEMPLATE_METADATA` if `remove_templates=true`.

# Arguments

  * `dir_templates::Union{String, Nothing}`: The directory path to load templates from. If `nothing`, uses the default list of paths. It usually used only once "to register" a new template storage.
  * `remember_path::Bool=true`: If true, remembers the path for future refresh (in `TEMPLATE_PATH`).
  * `remove_templates::Bool=isnothing(dir_templates)`: If true, removes any existing templates and metadata from `store` and `metadata_store`.
  * `store::Dict{Symbol, <:Any}=TEMPLATE_STORE`: The store to load the templates into.
  * `metadata_store::Vector{<:AITemplateMetadata}=TEMPLATE_METADATA`: The metadata store to load the metadata into.

# Example

Load the default templates:

```julia
PT.load_templates!() # no path needed
```

Load templates from a new custom path:

```julia
PT.load_templates!("path/to/templates") # we will remember this path for future refresh
```

If you want to now refresh the default templates and the new path, just call `load_templates!()` without any arguments.
