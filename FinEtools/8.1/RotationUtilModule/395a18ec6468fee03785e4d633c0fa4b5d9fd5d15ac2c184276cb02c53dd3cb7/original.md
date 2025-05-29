```
cross3!(
    result::AbstractVector{T1},
    theta::Union{AbstractVector{T2}, Tuple{T2, T2, T2}},
    v::Union{AbstractVector{T3}, Tuple{T3, T3, T3}}
) where {T1, T2, T3}
```

Compute the cross product of two vectors in three-space in place.
