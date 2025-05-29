```
show_texpr([io::IO,], ex)
```

また別の `Meta.show_sexpr`。これは式 `ex` をリスプスタイルの式として表示します。

注: インデントは `Meta.show_sexpr` とは異なります。

# 例

```julia
julia> show_texpr(:(f(x, g(y, z))))
Expr(:call, :f, :x, 
    Expr(:call, :g, :y, :z))
```
