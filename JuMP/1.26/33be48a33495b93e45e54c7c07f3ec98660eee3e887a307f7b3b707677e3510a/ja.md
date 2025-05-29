```
op_strictly_less_than(x, y)
```

`x < y` にフォールバックする関数ですが、JuMP 変数や式で呼び出された場合は [`GenericNonlinearExpr`](@ref) を返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> op_strictly_less_than(1, 2)
true

julia> op_strictly_less_than(x, 2)
x < 2
```
