```
show_texpr([io::IO,], ex)
```

Yet another `Meta.show_sexpr`.  It shows expression `ex` as a lisp style expression.

Remark: The indentation is different from `Meta.show_sexpr`.

# Examples

```julia
julia> show_texpr(:(f(x, g(y, z))))
Expr(:call, :f, :x, 
    Expr(:call, :g, :y, :z))
```
