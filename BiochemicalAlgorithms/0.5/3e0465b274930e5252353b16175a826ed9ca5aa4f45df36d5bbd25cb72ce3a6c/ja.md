```
AtomTable{T} <: AbstractSystemComponentTable{T}
```

システム原子（またはそのサブセット）のTables.jl互換表現。原子テーブルは[`atoms`](@ref)を使用して生成するか、他の原子テーブルからフィルタリングすることができます（`Base.filter`を介して）。

# 公開列

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

# 非公開列

  * `properties::AbstractVector{Properties}`
  * `flags::AbstractVector{Flags}`
  * `frame_id::AbstractVector{Int}`
  * `molecule_idx::AbstractVector{MaybeInt}`
  * `chain_idx::AbstractVector{MaybeInt}`
  * `fragment_idx::AbstractVector{MaybeInt}`
