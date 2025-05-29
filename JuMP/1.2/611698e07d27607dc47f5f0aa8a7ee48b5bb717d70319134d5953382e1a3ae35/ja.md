```
delete(model::Model, variable_ref::VariableRef)
```

`variable_ref`に関連付けられた変数をモデル`model`から削除します。

`delete`はモデルから名前を登録解除しないため、同じ名前の新しい変数を追加するとエラーが発生します。削除後に名前を登録解除するには、次のように[`unregister`](@ref)を使用してください。

```julia
@variable(model, x)
delete(model, x)
unregister(model, :x)
```

関連情報: [`unregister`](@ref)
