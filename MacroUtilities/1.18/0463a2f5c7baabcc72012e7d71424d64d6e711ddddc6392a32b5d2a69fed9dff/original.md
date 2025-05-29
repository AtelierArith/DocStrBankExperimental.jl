```
StructDefHeader(; typename, parameters, supertype)
```

Matches the header of a struct definition

# Fields

  * `typename::Symbol`
  * `parameters::Vector{TypeVarExpr} = TypeVarExpr[]`
  * `supertype::Union{Symbol, Expr, NotProvided} = not_provided`
