```
angle_between_vectors(
    v1::AbstractVector{T1}, v2::AbstractVector{T2}
) where {T1<:Number,T2<:Number}
```

Computes the angle between two vectors in a more numerically stable way than dot product.

# Arguments

-`v1::AbstractVector{<:Number}`: The first vector of the computation -`v2::AbstractVector{<:Number}`: The second vector of the computation

# Returns

-`angle::Number`: The angle between the two vectors
