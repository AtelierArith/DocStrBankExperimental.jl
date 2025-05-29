```
op_ifelse(a, x, y)
```

`ifelse(a, x, y)`にフォールバックする関数ですが、最初の引数にJuMP変数または式が渡された場合、[`GenericNonlinearExpr`](@ref)を返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> op_ifelse(true, 1.0, 2.0)
1.0

julia> op_ifelse(x, 1.0, 2.0)
ifelse(x, 1.0, 2.0)

julia> op_ifelse(true, x, 2.0)
x
```
