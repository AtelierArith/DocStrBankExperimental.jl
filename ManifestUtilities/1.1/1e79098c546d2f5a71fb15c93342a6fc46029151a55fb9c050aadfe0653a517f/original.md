```
prune_manifest(io::IO; kwargs...)
```

Parse the given project and manifest, and generate a new manifest that only includes packages that are direct or indirect (recursive) dependencies of the given project. The new manifest is printed to the given `IO`.

## Required Keyword Arguments

You must specify one (and exactly one) of `project` and `project_filename`. Similarly, you must specify one (and exactly one) of `manifest` and `manifest_filename`.

  * `project::Union{AbstractString, IO}`: the contents of the input `Project.toml` file
  * `project_filename::AbstractString`: the filename of the input `Project.toml` file
  * `manifest::Union{AbstractString, IO}`: the contents of the input `Manifest.toml` file
  * `manifest_filename::AbstractString`: the filename of the input `Manifest.toml` file
