```
departure_functions(model::MultiFluid)
```

もしモデルが `EmpiricDeparture` 出発モデルを使用している場合、出発関数の行列を返します。出発を次のように設定できます：

```
using CoolProp #CoolPropモデルをロード
model = MultiFluid(["helium","methanol"],mixing = LorentzBerthelotMixing)
dep_mat = departure_functions(model)

dep = Dict(
    #縮約CoolProp出発形式、タイプとパラメータのみが必要です。
    #ResidualHelmholtzPowerも機能します。
    type => "Exponential",
    n => [1,1,1,1],
    t => [1,1,1,1],
    d => [1,1,1,1],
    l => [1,1,1,1],
)


dep_mat[1,2] = create_departure(dep,F)

#if you want to delete a departure model:

dep_mat[1,2] = nothing
using SparseArrays
```
