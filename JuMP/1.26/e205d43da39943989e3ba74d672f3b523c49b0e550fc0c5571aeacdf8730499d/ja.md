```
all_variables(model::GenericModel{T})::Vector{GenericVariableRef{T}} where {T}
```

モデル内のすべての変数のリストを返します。変数は作成時間順に並べられています。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @variable(model, y);

julia> all_variables(model)
2-element Vector{VariableRef}:
 x
 y
```
