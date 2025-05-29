```
subs(p, s::AbstractSubstitution...)
```

Apply the substitutions `s` to `p`. Use `p(s...)` if we are sure that all the variables are substited in `s`.

The allowed substutions are:

  * `v => p` where `v` is a variable and `p` a polynomial, e.g. `x => 1` or `x => x^2*y + x + y`.
  * `V => P` where `V` is a tuple or vector of variables and `P` a tuple or vector of polynomials, e.g. `(x, y) => (y, x)` or `(y, x) => (2, 1)`.

The order of the variables is lexicographic with the name with TypedPolynomials and by order of creation with DynamicPolynomials. Since there is no guarantee on the order of the variables, substitution directly with a tuple or a vector is not allowed. You can use `p(variables(p) => (1, 2))` instead if you are sure of the order of the variables (e.g. the name order matches the creation order).

### Examples

```julia
p = 3x^2*y + x + 2y + 1
p(x => 2, y => 1) # Return type is Int
subs(p, x => 2, y => 1) # Return type is Int in TypedPolynomials but is a polynomial of Int coefficients in DynamicPolynomials
subs(p, y => x*y^2 + 1)
p(y => 2) # Do not do that, this works fine with TypedPolynomials but it will not return a correct result with DynamicPolynomials since it thinks that the return type is `Int`.
```
