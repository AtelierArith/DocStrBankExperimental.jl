```
variable_union_type(p::AbstractPolynomialLike)
```

Return the supertype for variables of `p`. If `p` is a variable, it should not be the type of `p` but the supertype of all variables that could be created.

### Examples

For `TypedPolynomials`, a variable of name `x` has type `Variable{:x}` so `variable_union_type` should return `Variable`. For `DynamicPolynomials`, all variables have the same type `Variable{C}` where `C` is `true` for commutative variables and `false` for non-commutative ones so `variable_union_type` should return `Variable{C}`.
