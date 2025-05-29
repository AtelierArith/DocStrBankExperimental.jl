```
domain(a::Tuple{T, Bool}, b::Tuple{T, Bool}) where {T <: Real}
domain(intervals::Vector{Tuple{Tuple{T, Bool},Tuple{T, Bool}}}) where {T <: Real}
```

連続区間のドメインを構築します。
