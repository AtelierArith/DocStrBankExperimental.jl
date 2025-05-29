```
terms(x)
```

Get the terms of the symbolic expression `x`.

# Examples

```julia-repl
julia> terms(-x + y - z)
3-element Vector{Num}:
 -z
  y
 -x
```
