```
ldrs(A::AbstractMatrix{T}, N::Int, ws::LDRWorkspace{T,E}) where {T,E}
```

Return a vector of [`LDR`](@ref) factorizations of length `N`, where each one represents the matrix `A`.
