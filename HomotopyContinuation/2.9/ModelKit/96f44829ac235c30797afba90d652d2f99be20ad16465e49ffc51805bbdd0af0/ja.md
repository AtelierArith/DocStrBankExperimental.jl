```
Expression <: Number
```

シンボリック式。

```julia-repl
julia> expr = (Variable(:x) + 1)^2
(1 + x)^2

julia> Expression(2)
2

julia> Expression(Variable(:x))
x
```
