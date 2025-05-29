```
SecondaryStructureTable{T} <: AbstractSystemComponentTable{T}
```

Tables.jl-compatible representation of system secondary structures (or a subset thereof). Secondary structure tables can be generated using [`secondary_structures`](@ref) or filtered from other secondary structure tables (via `Base.filter`).

# Public columns

  * `idx::AbstractVector{Int}`
  * `number::Int`
  * `type::SecondaryStructureType`
  * `name::AbstractVector{String}`

# Private columns

  * `properties::AbstractVector{Properties}`
  * `flags::AbstractVector{Flags}`
  * `molecule_idx::AbstractVector{Int}`
  * `chain_idx::AbstractVector{Int}`
