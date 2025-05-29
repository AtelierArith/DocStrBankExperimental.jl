```
delete(model::GenericModel, variable_ref::GenericVariableRef)
```

`variable_ref`に関連付けられた変数をモデル`model`から削除します。

`delete`はモデルから名前を登録解除しないため、同じ名前の新しい変数を追加するとエラーが発生します。削除後に名前を登録解除するには[`unregister`](@ref)を使用してください。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> delete(model, x)

julia> unregister(model, :x)

julia> print(model)
Feasibility
Subject to

julia> model[:x]
ERROR: KeyError: key :x not found
Stacktrace:
[...]
```
