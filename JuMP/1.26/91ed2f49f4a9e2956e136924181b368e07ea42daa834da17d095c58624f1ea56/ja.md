```
is_valid(model::GenericModel, variable_ref::GenericVariableRef)
```

`model`内の有効な変数を参照している場合、`true`を返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> is_valid(model, x)
true

julia> model_2 = Model();

julia> is_valid(model_2, x)
false
```
