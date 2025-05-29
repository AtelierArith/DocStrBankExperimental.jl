```
ChainTable{T} <: AbstractSystemComponentTable{T}
```

Tables.jl-compatible representation of system chains (or a subset thereof). Chain tables can be generated using [`chains`](@ref) or filtered from other chain tables (via `Base.filter`).

# Public columns

  * `idx::AbstractVector{Int}`
  * `name::AbstractVector{String}`

# Private columns

  * `properties::AbstractVector{Properties}`
  * `flags::AbstractVector{Flags}`
  * `molecule_idx::AbstractVector{Int}`
