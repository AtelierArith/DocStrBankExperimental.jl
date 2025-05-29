```
show_expr([io::IO,], ex)
```

は、式 `ex` をJuliaスタイルの式として表示します。

# 例

```julia
julia> show_expr(:(f(x, g(y, z))))
Expr(:call, :f, :x, 
    Expr(:call, :g, :y, :z))
```
