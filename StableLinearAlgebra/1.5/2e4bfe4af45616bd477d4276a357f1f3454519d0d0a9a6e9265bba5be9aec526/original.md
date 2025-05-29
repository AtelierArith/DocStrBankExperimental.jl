```
ldrs(A::AbstractArray{T,3}, ws::LDRWorkspace{T,E}) where {T,E}
```

Return a vector of [`LDR`](@ref) factorizations of length `size(A, 3)`, where there is an [`LDR`](@ref) factorization for each matrix `A[:,:,i]`.
