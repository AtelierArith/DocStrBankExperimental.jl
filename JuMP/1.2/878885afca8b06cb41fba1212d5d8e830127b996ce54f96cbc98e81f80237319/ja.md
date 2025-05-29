```
delete(model::Model, con_ref::ConstraintRef)
```

`constraint_ref`に関連付けられた制約をモデル`model`から削除します。

`delete`はモデルから名前を登録解除しないため、同じ名前の新しい制約を追加するとエラーが発生します。削除後に名前を登録解除するには、次のように[`unregister`](@ref)を使用してください。

```julia
@constraint(model, c, 2x <= 1)
delete(model, c)
unregister(model, :c)
```

参照: [`unregister`](@ref)
