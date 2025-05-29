```
bias(sim::OutputVar, obs::OutputVar; mask = nothing)
```

`sim`と`obs`のデータのバイアス（`sim.data - obs.data`）を持つ`OutputVar`を返し、経度と緯度にわたる`sim`と`obs`のデータのグローバルバイアスを計算します。結果は`var.attributes["global_bias"]`に格納されます。

この関数は現在、経度と緯度のみの次元を持つ`OutputVar`に対して実装されています。`sim`と`obs`のデータと次元には単位を指定する必要があります。経度と緯度の単位は度である必要があります。リサンプリングは、`obs`を`sim`にリサンプリングすることによって自動的に行われます。`sim`と`obs`の属性は破棄されます。返される`OutputVar`のロングネームとショートネームは、バイアスが計算されたことを反映するように更新されます。

パラメータ`mask`は`OutputVar`をマスクする関数です。[`apply_landmask`](@ref)および[`apply_oceanmask`](@ref)を参照してください。

また、[`global_bias`](@ref)、[`squared_error`](@ref)、[`global_mse`](@ref)、[`global_rmse`](@ref)も参照してください。
