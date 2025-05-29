```
y = circulant_attention(A::Circulant, x::AbstractArray)
y = A ⊗ x # \otimes
```

Applies circulant matrix `A` to `x`. See also [`circulant_adjacency`](@ref).
