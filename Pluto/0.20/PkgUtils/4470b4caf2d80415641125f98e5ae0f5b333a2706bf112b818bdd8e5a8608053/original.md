```julia
will_use_pluto_pkg(notebook_path::String)::Bool
```

Will this notebook use the Pluto package manager? `false` means that the notebook contains `Pkg.activate` or another deactivator.
