```
y = circulant_mh_attention(A::Circulant, x::AbstractArray)
y = A ⨷ x # \Otimes
```

Applies circulant matrix `A` (with channel dimension > 1) to `x`. See also [`circulant_attention`](@ref), [`circulant_adjacency`](@ref).
