```
BondTable{T} <: AbstractSystemComponentTable{T}
```

Tables.jl-compatible representation of system bonds (or a subset thereof). Bond tables can be generated using [`bonds`](@ref) or filtered from other bond tables (via `Base.filter`).

# Public columns

  * `idx::AbstractVector{Int}`
  * `a1::AbstractVector{Int}`
  * `a2::AbstractVector{Int}`
  * `order::AbstractVector{BondOrderType}`

# Private columns

  * `properties::AbstractVector{Properties}`
  * `flags::AbstractVector{Flags}`
