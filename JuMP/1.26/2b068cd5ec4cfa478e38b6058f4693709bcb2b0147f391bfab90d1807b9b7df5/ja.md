```
coefficient(a::GenericQuadExpr{C,V}, v::V) where {C,V}
```

変数 `v` に関連付けられた係数を `a` のアフィン成分から返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> expr = 2.0 * x^2 + 3.0 * x;

julia> coefficient(expr, x)
3.0
```
