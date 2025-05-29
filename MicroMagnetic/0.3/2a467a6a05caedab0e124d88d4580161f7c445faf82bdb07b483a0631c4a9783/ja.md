```
save_vtk(sim::AbstractSim, fname::String; fields::Array{String, 1} = String[])
```

磁化または他のフィールドをvtkに保存します。

```julia
    save_vtk(sim, "m")
```
