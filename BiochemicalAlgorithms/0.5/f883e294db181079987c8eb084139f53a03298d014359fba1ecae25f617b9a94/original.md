```
FragmentTable{T} <: AbstractSystemComponentTable{T}
```

Tables.jl-compatible representation of system fragments (or a subset thereof). Fragment tables can be generated using [`fragments`](@ref) or filtered from other fragment tables (via `Base.filter`).

# Public columns

  * `idx::AbstractVector{Int}`
  * `number::AbstractVector{Int}`
  * `name::AbstractVector{String}`

# Private columns

  * `variant::AbstractVector{FragmentVariantType}`
  * `properties::AbstractVector{Properties}`
  * `flags::AbstractVector{Flags}`
  * `molecule_idx::AbstractVector{Int}`
  * `chain_idx::AbstractVector{Int}`
