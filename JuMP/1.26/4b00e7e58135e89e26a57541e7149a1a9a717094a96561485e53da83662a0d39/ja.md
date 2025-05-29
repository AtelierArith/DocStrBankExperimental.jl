```
op_and(x, y)
```

`x & y` にフォールバックする関数ですが、JuMP 変数または式で呼び出された場合は [`GenericNonlinearExpr`](@ref) を返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> op_and(true, false)
false

julia> op_and(true, x)
true && x
```
