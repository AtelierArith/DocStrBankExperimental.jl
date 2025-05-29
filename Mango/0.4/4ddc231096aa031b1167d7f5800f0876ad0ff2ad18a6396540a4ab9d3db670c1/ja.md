```
get_model(role::Role, type::DataType)
```

プールから共有モデルを取得します。モデルがまだ存在しない場合は、作成されます。デフォルトコンストラクタを持つタイプのみが許可されています！

# 例

```julia
@kwdef struct ExampleModel
    my_field::Int = 0
end
role = ExampleRole()
model::ExampleModel = get_model(role, ExampleModel)
model.my_field = 1
model2::ExampleModel = get_model(role, ExampleModel)
# model == model2、すべてのロールに対しても同じになります！
```
