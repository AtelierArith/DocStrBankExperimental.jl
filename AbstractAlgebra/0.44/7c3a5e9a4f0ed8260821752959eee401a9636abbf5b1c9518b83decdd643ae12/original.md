```
howell_form_with_transformation(A::MatElem{<:RingElement}; reduced::Bool = true, shape::Symbol = :upper)
```

Return a Howell form $H$ of $A$ and a matrix $U$ with $H = UA$. Notice that $H$ may have more rows than $A$ and hence $U$ may not be invertible. It is assumed that `base_ring(A)` is a principal ideal ring

See [`hermite_form`](@ref) for the keyword arguments.
