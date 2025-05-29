```
modelsummary(m::AbstractMillModel)
```

モデル `m` のパラメータの要約を印刷します。

# 例

```jldoctest
julia> m = ProductModel(ArrayModel(Dense(2, 3)))
ProductModel ↦ identity
  ╰── ArrayModel(Dense(2 => 3))  2 arrays, 9 params, 124 bytes

julia> modelsummary(m)
"Model summary: 2 arrays, 9 params, 124 bytes"
```

参照: [`datasummary`](@ref).
