```
substitute(p::Polynomial, i, x)
```

In `p` substitute for the variable with index `i` the value `x`. You can use this for partial evaluation of polynomial.

### Example

```julia-repl
julia> substitute(x^2+3y, 2, 5)
x^2+15
```
