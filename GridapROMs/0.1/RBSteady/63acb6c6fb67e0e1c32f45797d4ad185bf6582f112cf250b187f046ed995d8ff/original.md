```
struct TTSVDProjection <: Projection
  cores::AbstractVector{<:AbstractArray{T,3} where T}
  dof_map::AbstractDofMap
end
```

Projection stemming from a tensor train SVD [`ttsvd`](@ref). For reindexing purposes a field `dof_map` is provided along with the tensor train cores `cores`
