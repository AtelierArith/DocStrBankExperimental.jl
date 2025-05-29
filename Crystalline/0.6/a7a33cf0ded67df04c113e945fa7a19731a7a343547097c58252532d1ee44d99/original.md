```
SymmetryVector(
    nv :: AbstractVector{<:Integer},
    irlabs_nv :: AbstractVector{<:AbstractString},
    lgirsd :: AbstractDict{String, <:AbstractVector{LGIrrep{D}}}) --> SymmetryVector{D}
```

Build a structured `SymmetryVector` representation of a "raw" vector `nv` of irrep multiplicities, whose `i`th element gives the irrep multiplicity of the irrep whose label  is `irlabs_nv[i]`. The corresponding full irrep information is inferred by comparison of labels in `irlabs_nv` and a provided set of covering irreps in `lgirsd`.

The raw vector `nv` must contain its band occupation number as its last element. The `irlabs_nv` vector must consequently have length `length(nv)-1`.

The sorting of irrep labels in `lgirsd` and (`nv`, `irlabs_nv`) is allowed to differ: this is the main utility of the function: to map between differently sorted raw vectors and a structured irrep storage in `lgirsd`.
