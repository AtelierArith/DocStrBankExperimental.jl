```
MoleculeTable{T} <: AbstractSystemComponentTable{T}
```

システム分子（またはそのサブセット）の Tables.jl 互換表現。分子テーブルは [`molecules`](@ref) を使用して生成するか、他の分子テーブルからフィルタリングすることができます（`Base.filter` を介して）。

# 公開カラム

  * `idx::AbstractVector{Int}`
  * `name::AbstractVector{String}`

# 非公開カラム

  * `variant::AbstractVector{MoleculeVariantType}`
  * `properties::AbstractVector{Properties}`
  * `flags::AbstractVector{Flags}`
