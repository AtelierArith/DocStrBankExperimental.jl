```
Projection
```

Data type for projection of wave function.

# Fields

  * `number_kpoints::Integer`: stores the number of k-points
  * `number_bands::Integer`: stores the number of bands
  * `number_ions::Integer`: stores the number of ions
  * `projection::Array{<:Complex, 4}`: stores the projection ⟨Yₗₘ|ϕₙₖ⟩. The index order is   [kpoint number, band number, ion number, orbit number]
  * `projection_square::Array{<:Real, 4}`: stores the squared projection |⟨Yₗₘ|ϕₙₖ⟩|². The   index order is same as `projection`.
