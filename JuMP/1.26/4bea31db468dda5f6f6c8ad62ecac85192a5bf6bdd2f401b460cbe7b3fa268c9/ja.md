```
coefficient(a::GenericAffExpr{C,V}, v::V) where {C,V}
```

変数 `v` に関連付けられた係数をアフィン式 `a` から返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> expr = 2.0 * x + 1.0;

julia> coefficient(expr, x)
2.0
```
