```
ldrs!(Fs::AbstractVector{LDR{T,E}}, A::AbstractArray{T,3}, ws::LDRWorkspace{T,E}) where {T,E}
```

Calculate the [`LDR`](@ref) factorization `Fs[i]` for the matrix `A[:,:,i]`.
