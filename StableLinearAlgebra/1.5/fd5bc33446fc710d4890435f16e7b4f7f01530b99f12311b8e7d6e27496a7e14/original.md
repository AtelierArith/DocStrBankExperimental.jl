```
ldrs(A::AbstractMatrix{T}, N::Int) where {T}
```

Return a vector of [`LDR`](@ref) factorizations of length `N`, where each one represents the identity matrix of the same size as $A$.
