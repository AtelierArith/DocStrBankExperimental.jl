```
echelon_form_with_transformation(A::MatElem{<:FieldElement}; reduced::Bool = true, shape::Symbol = :upper)
```

Return a row echelon form $R$ of $A$ and an invertible matrix $U$ with $R = UA$.

See [`echelon_form`](@ref) for the keyword arguments.
