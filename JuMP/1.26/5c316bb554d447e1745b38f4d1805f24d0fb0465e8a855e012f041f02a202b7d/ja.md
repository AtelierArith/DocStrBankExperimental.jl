```
op_or(x, y)
```

`x | y` にフォールバックする関数ですが、JuMP 変数または式で呼び出された場合は、[`GenericNonlinearExpr`](@ref) を返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> op_or(true, false)
true

julia> op_or(true, x)
true || x
```
