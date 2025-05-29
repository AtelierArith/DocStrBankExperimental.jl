```
VariableRef(c::ConstraintRef)
```

`ConstraintRef`に関連付けられた変数を取得します。`c`が単一の変数に対する制約である場合です。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0)
x

julia> c = LowerBoundRef(x)
x ≥ 0.0

julia> VariableRef(c) == x
true
```
