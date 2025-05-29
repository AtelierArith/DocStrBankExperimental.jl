```
euler_approx(rs::Vector{R}, args...) where {T,R<:ContinuousResourceSharer{T}}
euler_approx(rs::AbstractDict{S, R}, args...) where {S,T,R<:ContinuousResourceSharer{T}}
```

Map `euler_approx` over a collection of resource sharers with identical `args`.
