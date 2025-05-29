```
grow_dst!(dst::AbstractVector{UInt8}, max_size::Int64)::Union{Nothing, Int64}
```

Grow the destination vector `dst` to a size between its current size and `max_size`. Return the new size of `dst` if it was grown, or `nothing` if it could not be grown due to the `max_size` restriction.
