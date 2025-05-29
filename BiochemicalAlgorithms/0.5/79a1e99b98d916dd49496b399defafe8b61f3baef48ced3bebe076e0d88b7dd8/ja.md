```
BondTable{T} <: AbstractSystemComponentTable{T}
```

システムボンド（またはそのサブセット）のTables.jl互換表現。ボンドテーブルは[`bonds`](@ref)を使用して生成するか、他のボンドテーブルからフィルタリングすることができます（`Base.filter`を介して）。

# 公開列

  * `idx::AbstractVector{Int}`
  * `a1::AbstractVector{Int}`
  * `a2::AbstractVector{Int}`
  * `order::AbstractVector{BondOrderType}`

# 非公開列

  * `properties::AbstractVector{Properties}`
  * `flags::AbstractVector{Flags}`
