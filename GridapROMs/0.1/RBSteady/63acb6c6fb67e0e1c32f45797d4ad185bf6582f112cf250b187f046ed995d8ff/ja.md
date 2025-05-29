```
struct TTSVDProjection <: Projection
  cores::AbstractVector{<:AbstractArray{T,3} where T}
  dof_map::AbstractDofMap
end
```

テンソル列SVD [`ttsvd`](@ref) に由来するプロジェクション。再インデックス化の目的のために、テンソル列コア `cores` とともにフィールド `dof_map` が提供されます。
