```
name(v::GenericVariableRef)::String
```

変数の名前属性を取得します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2])
2-element Vector{VariableRef}:
 x[1]
 x[2]

julia> name(x[1])
"x[1]"
```
