```
drop_zeros!(expr::GenericQuadExpr)
```

係数が `0` の項を二次式から削除します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> expr = x[1]^2 + x[2]^2;

julia> add_to_expression!(expr, -1.0, x[1], x[1])
0 x[1]² + x[2]²

julia> drop_zeros!(expr)

julia> expr
x[2]²
```
