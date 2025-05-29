```
echelon_form(A::MatElem{<:FieldElement}; reduced::Bool = true, shape::Symbol = :upper, trim::Bool = false)
```

Return a row echelon form $R$ of $A$.

# Keyword arguments

  * `reduced`: Whether the columns of $R$ which contain a pivot are reduced. The default is `true`.
  * `shape`: Whether $R$ is an upper-right (`:upper`, default) or lower-left (`:lower`) echelon form.
  * `trim`: By default, $R$ will have as many rows as $A$ and potentially involve rows only containing zeros. If `trim = true`, these rows are removed, so that the number of rows of $R$ coincides with the rank of $A$.

See also [`echelon_form_with_transformation`](@ref).
