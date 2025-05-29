```
op_strictly_greater_than(x, y)
```

`x > y` にフォールバックする関数ですが、JuMP 変数または式で呼び出された場合は、[`GenericNonlinearExpr`](@ref) を返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> op_strictly_greater_than(1, 2)
false

julia> op_strictly_greater_than(x, 2)
x > 2
```
