```
convert(::Type{AbstractMatrix}, p::SPDPoint)
```

return the point `p` as a matrix. The matrix is either stored within the [`SPDPoint`](@ref) or reconstructed from `p.eigen`.
