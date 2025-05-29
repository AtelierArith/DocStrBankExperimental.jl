```
constant(quad::GenericQuadExpr{C,V})::C
```

二次式の定数を返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> quad = 2.0 * x^2 + 3.0;

julia> constant(quad)
3.0
```
