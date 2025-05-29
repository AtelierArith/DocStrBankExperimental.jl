`segment(v::Vector{T}, L::Int; overlap::Union{<:AbstractFloat,Integer}=0, symmetric=false) where {T}`

Splits a vector `v` into segments of length `L` with an overlap `overlap` expressed as a fraction of L. The `overlap` defaults to `0` (no overlap). Returns a vector $v$ of vectors - i.e. `Vector{Vector{T}}` - with $\vec{v_i}$ the $i$th segment in the split.

The function always attempts to capture the whole vector, even if the final split is not of length L. For example, 

```julia
> x = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
> segment(x, 5)
2-element Vector{Vector{Int64}}:
[1, 2, 3, 4, 5]
[6, 7, 8, 9, 0]

> segment(x, 7)
2-element Vector{Vector{Int64}}:
[1, 2, 3, 4, 5, 6, 7]
[8, 9, 0]
```

Set `symmetric=true` to ensure that, if this occurs, the last split is dropped.

```julia
> segment(x, 3; symmetric=true)
3-element Vector{Vector{Int64}}:
[1, 2, 3]
[4, 5, 6]
[7, 8, 9]
```

If `L` is equal to the segment length, `segment` raises a warning and returns a vector with only the original vector: `[v]`.  The return value ensures type-safety but the warning is raised because  splitting a vector over its length is potentially  a programming mistake.
