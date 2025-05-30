```
delete(model::GenericModel, con_ref::ConstraintRef)
```

`constraint_ref` に関連付けられた制約をモデル `model` から削除します。

`delete` はモデルから名前を登録解除しないため、同じ名前の新しい制約を追加するとエラーが発生します。削除後に名前を登録解除するには [`unregister`](@ref) を使用してください。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, c, 2x <= 1)
c : 2 x ≤ 1

julia> delete(model, c)

julia> unregister(model, :c)

julia> print(model)
Feasibility
Subject to

julia> model[:c]
ERROR: KeyError: key :c not found
Stacktrace:
[...]
```
