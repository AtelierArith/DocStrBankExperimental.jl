```
VectorOfVectors{T,...} = VectorOfArrays{T,1,...}
```

Constructors:

```julia
VectorOfVectors(A::AbstractVector{<:AbstractVector})
VectorOfVectors{T}(A::AbstractVector{<:AbstractVector}) where {T}

VectorOfVectors(
    data::AbstractVector, elem_ptr::AbstractVector{<:Integer},
    checks::Function = full_consistency_checks
)

See also [VectorOfArrays](@ref).
```
