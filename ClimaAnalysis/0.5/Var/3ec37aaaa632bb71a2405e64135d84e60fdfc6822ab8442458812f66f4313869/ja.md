```
squared_error(sim::OutputVar, obs::OutputVar; mask = nothing)
```

`OutputVar`を返し、そのデータは二乗誤差（`(sim.data - obs.data)^2`）であり、`sim`と`obs`の`data`に対する全体の平均二乗誤差（MSE）と全体の平方根平均二乗誤差（RMSE）を経度と緯度にわたって計算します。結果は`var.attributes["mse"]`と`var.attributes["rmse"]`に格納されます。

この関数は現在、経度と緯度のみの次元を持つ`OutputVar`に対して実装されています。`sim`と`obs`のデータと次元には単位を指定する必要があります。経度と緯度の単位は度である必要があります。リサンプリングは、`obs`を`sim`にリサンプリングすることによって自動的に行われます。`sim`と`obs`の属性は破棄されます。返される`OutputVar`の長い名前と短い名前は、二乗誤差が計算されていることを反映するように更新されます。

パラメータ`mask`は`OutputVar`をマスクする関数です。[`apply_landmask`](@ref)および[`apply_oceanmask`](@ref)を参照してください。

また、[`global_mse`](@ref)、[`global_rmse`](@ref)、[`bias`](@ref)、[`global_bias`](@ref)も参照してください。
