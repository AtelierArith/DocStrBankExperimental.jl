```
parse_constraint(_error::Function, expr::Expr)
```

The entry-point for all constraint-related parsing.

## Arguments

  * The `_error` function is passed everywhere to provide better error messages
  * `expr` comes from the `@constraint` macro. There are two possibilities:

      * `@constraint(model, expr)`
      * `@constraint(model, name[args], expr)`

    In both cases, `expr` is the main component of the constraint.

## Supported syntax

JuMP currently supports the following `expr` objects:

  * `lhs <= rhs`
  * `lhs == rhs`
  * `lhs >= rhs`
  * `l <= body <= u`
  * `u >= body >= l`
  * `lhs ⟂ rhs`
  * `lhs in rhs`
  * `lhs ∈ rhs`
  * `z => {constraint}`
  * `!z => {constraint}`

as well as all broadcasted variants.

## Extensions

The infrastructure behind `parse_constraint` is extendable. See [`parse_constraint_head`](@ref) and [`parse_constraint_call`](@ref) for details.
