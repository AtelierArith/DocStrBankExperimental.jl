```
hermite_form(A::MatElem{<:RingElement}; reduced::Bool = true, shape::Symbol = :upper, trim::Bool = false)
```

Return a Hermite normal form $H$ of $A$. It is assumed that `base_ring(A)` is euclidean.

# Keyword arguments

  * `reduced`: Whether the columns of $H$ which contain a pivot are reduced. The default is `true`.
  * `shape`: Whether $H$ is an upper-right (`:upper`, default) or lower-left (`:lower`) echelon form.
  * `trim`: By default, $H$ will have as many rows as $A$ and potentially involve rows only containing zeros. If `trim = true`, these rows are removed, so that the number of rows of $H$ coincides with the rank of $A$.

See also [`hermite_form_with_transformation`](@ref).
