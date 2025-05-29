```
howell_form(A::MatElem{<:RingElement}; reduced::Bool = true, shape::Symbol = :upper, trim::Bool = false)
```

Return a Howell form $H$ of $A$. It is assumed that `base_ring(A)` is a principal ideal ring.

# Keyword arguments

  * `reduced`: Whether the columns of $H$ which contain a pivot are reduced. The default is `true`.
  * `shape`: Whether $H$ is an upper-right (`:upper`, default) or lower-left (`:lower`) echelon form.
  * `trim`: By default, $H$ will have at least as many rows as $A$ and potentially involve rows only containing zeros. If `trim = true`, these rows are removed.

See also [`howell_form_with_transformation`](@ref).
