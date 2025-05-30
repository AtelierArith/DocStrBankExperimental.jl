```julia
activate_notebook_environment(f::Function, notebook_path::String)
```

Temporarily activate the package environment embedded in a notebook file, for use inside scripts. Inside your function `f`, you can use Pkg commands to modify the environment, and any changes you make will be automatically saved in the notebook file after your function finishes. Not thread-safe.

This method is best for scripts that update notebook files. For interactive use, the method `activate_notebook_environment(notebook_path::String)` is recommended.

# Example

```julia
Pluto.activate_notebook_environment("notebook.jl") do
    Pkg.add("Example")
end

# Now the file "notebook.jl" was updated!
```

!!! warning
    This function uses the private method `Pkg.activate(f::Function, path::String)`. This API might not be available in future Julia versions. 🤷

