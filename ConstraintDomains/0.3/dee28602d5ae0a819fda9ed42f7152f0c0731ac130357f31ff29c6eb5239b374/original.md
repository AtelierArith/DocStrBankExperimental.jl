```
domain(a::Tuple{T, Bool}, b::Tuple{T, Bool}) where {T <: Real}
domain(intervals::Vector{Tuple{Tuple{T, Bool},Tuple{T, Bool}}}) where {T <: Real}
```

Construct a domain of continuous interval(s).
