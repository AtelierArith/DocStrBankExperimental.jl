```julia
reset_notebook_environment(notebook_path::String; keep_project::Bool=false, backup::Bool=true)
```

Remove the embedded `Project.toml` and `Manifest.toml` from a notebook file, modifying the notebook file. If `keep_project` is true, only `Manifest.toml` will be deleted. A backup of the notebook file is created by default.
