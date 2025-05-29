```
goldensection(f, (a, b); [tol=eps()])
```

Finds argmin of function `f(x)` on `a < x < b`.

## Examples

```julia-repl
julia> goldensection(x-> (x-2)^2, (-4, 4))
2.0
```
