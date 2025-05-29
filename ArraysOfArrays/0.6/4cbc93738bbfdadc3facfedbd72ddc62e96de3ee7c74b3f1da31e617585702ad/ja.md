```
VectorOfVectors{T,...} = VectorOfArrays{T,1,...}
```

コンストラクタ:

```julia
VectorOfVectors(A::AbstractVector{<:AbstractVector})
VectorOfVectors{T}(A::AbstractVector{<:AbstractVector}) where {T}

VectorOfVectors(
    data::AbstractVector, elem_ptr::AbstractVector{<:Integer},
    checks::Function = full_consistency_checks
)

参照: [VectorOfArrays](@ref).
```
