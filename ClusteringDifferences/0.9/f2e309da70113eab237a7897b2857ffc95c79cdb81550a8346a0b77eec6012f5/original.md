```
kmeans(X::AbstractMatrix{<:Real}, μ::AbstractMatrix{<:Real}; <keyword arguments>)
```

Like [`kmeans`](@ref), but automatically generate `r` and `c` according to the size of `X`.
