```
FormulaTerm{L,R} <: AbstractTerm
```

Represents an entire formula, with a left- and right-hand side.  These can be of any type (captured by the type parameters).

# Fields

  * `lhs::L`: The left-hand side (e.g., response)
  * `rhs::R`: The right-hand side (e.g., predictors)
