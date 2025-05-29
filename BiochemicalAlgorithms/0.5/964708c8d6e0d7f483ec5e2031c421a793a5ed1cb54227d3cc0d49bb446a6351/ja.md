```
ChainTable{T} <: AbstractSystemComponentTable{T}
```

システムチェーン（またはそのサブセット）のTables.jl互換表現。チェーンテーブルは[`chains`](@ref)を使用して生成するか、他のチェーンテーブルからフィルタリングすることができます（`Base.filter`を介して）。

# 公開カラム

  * `idx::AbstractVector{Int}`
  * `name::AbstractVector{String}`

# 非公開カラム

  * `properties::AbstractVector{Properties}`
  * `flags::AbstractVector{Flags}`
  * `molecule_idx::AbstractVector{Int}`
