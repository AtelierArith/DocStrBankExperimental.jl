```
op_less_than_or_equal_to(x, y)
```

`x <= y` にフォールバックする関数ですが、JuMP 変数または式で呼び出された場合は、[`GenericNonlinearExpr`](@ref) を返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> op_less_than_or_equal_to(2, 2)
true

julia> op_less_than_or_equal_to(x, 2)
x <= 2
```
