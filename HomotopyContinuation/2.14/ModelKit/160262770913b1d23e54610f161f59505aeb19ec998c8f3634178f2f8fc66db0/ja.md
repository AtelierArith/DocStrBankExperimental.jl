```
expand(e::Expression)
```

与えられた式を展開します。

```julia-repl
julia> @var x y
(x, y)

julia> expand((x + y) ^ 2)
2*x*y + x^2 + y^2
```
