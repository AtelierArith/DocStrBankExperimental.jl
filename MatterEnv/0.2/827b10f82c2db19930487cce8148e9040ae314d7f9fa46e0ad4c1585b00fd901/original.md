```
save_procar(projection::Projection,
    kpoints::Array{KPoint, 1},
    bands::AbstractBands,
    filename::String="PROCAR";
    squared_only::Bool=true)
```

Save projection of wave function ⟨Yₗₘ|ϕₙₖ⟩ into PROCAR file.

# Arguments

  * `projection::AbstractProjection`: projection of wave function
  * `kpoints::Array{KPoint, 1}`: metadata of k-points
  * `bands::AbstractBands`: metadata of bands
  * `filename::String="PROCAR"`: name of output file
  * `squared_only::Bool=true`: only output squared projection |⟨Yₗₘ|ϕₙₖ⟩|² or not
