```
TypeVarExpr <: AbstractExpr
```

Matches expressions of the form

  * `typename`
  * `typename <: UB`
  * `<: UB`
  * `typename >: LB`
  * `>: LB`
  * `LB <: typename <: UB`

## Constructors

```
    TypeVarExpr{LB, UB}(; typename::Symbol, lb::Union{LB, NotProvided}=not_provided, ub::Union{UB, NotProvided}=not_provided)

    TypeVarExpr(typename::Symbol, [lb], [ub])

    TypeVarExpr{LB, UB}(t::TypeVarExpr)
```
