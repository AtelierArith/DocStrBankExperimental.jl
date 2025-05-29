```julia
struct FunctionalTable{C<:NamedTuple, O<:Tuple{Vararg{FunctionalTables.ColumnOrdering}}}
```

# Internal notes

  * Use accessors `length`, `colums`, and `ordering` to access the fields, property accessors are forwarded to `columns`.
  * The only inner constructor is the one where both the length and the ordering is trusted (and thus unchecked). Outer constructors should first wrap the ordering rule, then compute/verify length.
