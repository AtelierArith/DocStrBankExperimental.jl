```
bias(::Type{Floatmu{szE,szf}}) where {szE, szf}
```

`Floatmu{szE,szf}` の指数のバイアス。

# 例

```jldoctest
julia> bias(Floatmu{8, 23}) 
0x0000007f
```
