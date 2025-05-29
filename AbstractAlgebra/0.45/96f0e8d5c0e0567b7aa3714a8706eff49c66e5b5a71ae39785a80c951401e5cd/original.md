```
hermite_form_with_transformation(A::MatElem{<:RingElement}; reduced::Bool = true, shape::Symbol = :upper)
```

Return a Hermite normal form $H$ of $A$ and an invertible matrix $U$ with $H = UA$. It is assumed that `base_ring(A)` is euclidean.

See [`hermite_form`](@ref) for the keyword arguments.
