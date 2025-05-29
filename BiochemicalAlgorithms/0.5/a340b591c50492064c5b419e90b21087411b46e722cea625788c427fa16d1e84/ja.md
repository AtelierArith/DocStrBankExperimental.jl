```
SecondaryStructureTable{T} <: AbstractSystemComponentTable{T}
```

Tables.jl互換のシステム二次構造（またはそのサブセット）の表現。二次構造テーブルは[`secondary_structures`](@ref)を使用して生成するか、他の二次構造テーブルからフィルタリングすることができます（`Base.filter`を介して）。

# 公開カラム

  * `idx::AbstractVector{Int}`
  * `number::Int`
  * `type::SecondaryStructureType`
  * `name::AbstractVector{String}`

# 非公開カラム

  * `properties::AbstractVector{Properties}`
  * `flags::AbstractVector{Flags}`
  * `molecule_idx::AbstractVector{Int}`
  * `chain_idx::AbstractVector{Int}`
