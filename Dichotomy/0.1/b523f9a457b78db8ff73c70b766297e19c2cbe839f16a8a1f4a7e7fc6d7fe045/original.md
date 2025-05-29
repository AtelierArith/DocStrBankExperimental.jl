```
bisection(f, (a, b); [tol=eps()])
```

Finds root of equation `f(x) = 0` on `a < x < b`.

Method works only if `f(a) * f(b) < 0`.

## Examples

```julia-repl
julia> bisection(sin, (2, 4))
3.141592653589793
```
