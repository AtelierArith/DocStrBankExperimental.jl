```
compose(lhs::Symbol, rhs::Tuple)
compose(lhs::Symbol, rhs::Term)
compose(lhs::Symbol, rhs::ConstantTerm)
```

Compose a response variable `lhs` with a tuple or vector of predictors `rhs` terms.

# Arguments

  * `lhs::Symbol`: The left-hand side of the equation.
  * `rhs::Tuple`: The right-hand side of the equation.

# Returns

  * The composed equation.

If `rhs` is empty, the function returns `lhs` composed with an intercept. Otherwise, the function returns `lhs` composed with the terms in `rhs`.
