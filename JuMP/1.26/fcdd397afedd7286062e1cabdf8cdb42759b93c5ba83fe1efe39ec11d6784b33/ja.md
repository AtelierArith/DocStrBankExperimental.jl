```
constant(aff::GenericAffExpr{C,V})::C
```

アフィン式の定数を返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> aff = 2.0 * x + 3.0;

julia> constant(aff)
3.0
```
