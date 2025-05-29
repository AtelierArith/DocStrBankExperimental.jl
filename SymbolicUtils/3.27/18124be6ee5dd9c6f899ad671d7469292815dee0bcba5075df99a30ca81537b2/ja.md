```
substitute(expr, dict; fold=true)
```

`dict`のキーに一致する任意の部分式を対応する値で置き換えます。`fold=false`の場合、評価可能な式は評価されません。

```julia
julia> substitute(1+sqrt(y), Dict(y => 2), fold=true)
2.414213562373095
julia> substitute(1+sqrt(y), Dict(y => 2), fold=false)
1 + sqrt(2)
```
