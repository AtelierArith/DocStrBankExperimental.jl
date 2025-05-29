```
AtomTable{T} <: AbstractSystemComponentTable{T}
```

Tables.jl-compatible representation of system atoms (or a subset thereof). Atom tables can be generated using [`atoms`](@ref) or filtered from other atom tables (via `Base.filter`).

# Public columns

  * `idx::AbstractVector{Int}`
  * `number::AbstractVector{Int}`
  * `element::AbstractVector{ElementType}`
  * `name::AbstractVector{String}`
  * `atom_type::AbstractVector{String}`
  * `r::AbstractVector{Vector3{T}}`
  * `v::AbstractVector{Vector3{T}}`
  * `F::AbstractVector{Vector3{T}}`
  * `formal_charge::AbstractVector{Int}`
  * `charge::AbstractVector{T}`
  * `radius::AbstractVector{T}`

# Private columns

  * `properties::AbstractVector{Properties}`
  * `flags::AbstractVector{Flags}`
  * `frame_id::AbstractVector{Int}`
  * `molecule_idx::AbstractVector{MaybeInt}`
  * `chain_idx::AbstractVector{MaybeInt}`
  * `fragment_idx::AbstractVector{MaybeInt}`
