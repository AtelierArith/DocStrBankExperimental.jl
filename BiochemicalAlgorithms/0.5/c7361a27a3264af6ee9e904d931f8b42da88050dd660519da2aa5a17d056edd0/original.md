```
MoleculeTable{T} <: AbstractSystemComponentTable{T}
```

Tables.jl-compatible representation of system molecules (or a subset thereof). Molecule tables can be generated using [`molecules`](@ref) or filtered from other molecule tables (via `Base.filter`).

# Public columns

  * `idx::AbstractVector{Int}`
  * `name::AbstractVector{String}`

# Private columns

  * `variant::AbstractVector{MoleculeVariantType}`
  * `properties::AbstractVector{Properties}`
  * `flags::AbstractVector{Flags}`
