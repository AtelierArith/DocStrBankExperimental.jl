```
coefficient(a::GenericQuadExpr{C,V}, v1::V, v2::V) where {C,V}
```

二次式 `a` における項 `v1 * v2` に関連付けられた係数を返します。

`coefficient(a, v1, v2)` は `coefficient(a, v2, v1)` と同じです。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> expr = 2.0 * x[1] * x[2];

julia> coefficient(expr, x[1], x[2])
2.0

julia> coefficient(expr, x[2], x[1])
2.0

julia> coefficient(expr, x[1], x[1])
0.0
```
