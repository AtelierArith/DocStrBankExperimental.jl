```
show_expr([io::IO,], ex)
```

shows expression `ex` as a Julia style expression.

# Examples

```julia
julia> show_expr(:(f(x, g(y, z))))
Expr(:call, :f, :x, 
    Expr(:call, :g, :y, :z))
```
