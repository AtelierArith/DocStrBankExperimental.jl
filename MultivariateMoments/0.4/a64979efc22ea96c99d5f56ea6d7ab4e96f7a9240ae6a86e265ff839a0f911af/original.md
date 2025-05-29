```
measure(a::AbstractVector{T}, X::AbstractVector{<:AbstractMonomial}; rtol=Base.rtoldefault(T), atol=zero(T))
```

Creates a measure with moments `moment(a[i], X[i])` for each `i`. An error is thrown if there exists `i` and `j` such that `X[i] == X[j]` but `!isapprox(a[i], a[j]; rtol=rtol, atol=atol)`.
