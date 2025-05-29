```
expand(e::Expression)
```

Expand a given expression.

```julia-repl
julia> @var x y
(x, y)

julia> expand((x + y) ^ 2)
2*x*y + x^2 + y^2
```
