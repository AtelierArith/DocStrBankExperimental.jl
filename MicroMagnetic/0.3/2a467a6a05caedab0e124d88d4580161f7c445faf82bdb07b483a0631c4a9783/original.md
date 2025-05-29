```
save_vtk(sim::AbstractSim, fname::String; fields::Array{String, 1} = String[])
```

Save magnetization or other fields to vtk.

```julia
    save_vtk(sim, "m")
```
