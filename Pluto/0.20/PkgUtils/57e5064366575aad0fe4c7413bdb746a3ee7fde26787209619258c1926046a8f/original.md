```julia
update_notebook_environment(notebook_path::String; backup::Bool=true, level::Pkg.UpgradeLevel=Pkg.UPLEVEL_MAJOR)
```

Call `Pkg.update` in the package environment embedded in a notebook file, modifying the notebook file. A [`Pkg.UpgradeLevel`](@ref) can be passed to the `level` keyword argument. A backup file is created by default. 
