```
FragmentTable{T} <: AbstractSystemComponentTable{T}
```

システムフラグメント（またはそのサブセット）のTables.jl互換表現。フラグメントテーブルは[`fragments`](@ref)を使用して生成するか、他のフラグメントテーブルからフィルタリングすることができます（`Base.filter`を介して）。

# 公開カラム

  * `idx::AbstractVector{Int}`
  * `number::AbstractVector{Int}`
  * `name::AbstractVector{String}`

# 非公開カラム

  * `variant::AbstractVector{FragmentVariantType}`
  * `properties::AbstractVector{Properties}`
  * `flags::AbstractVector{Flags}`
  * `molecule_idx::AbstractVector{Int}`
  * `chain_idx::AbstractVector{Int}`
