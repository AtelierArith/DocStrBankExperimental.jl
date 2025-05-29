```
global_bias(sim::OutputVar, obs::OutputVar; mask = nothing)
```

`sim` と `obs` の `data` の全体的なバイアスを経度と緯度にわたって返します。

この関数は現在、経度と緯度のみの次元を持つ `OutputVar` に対してのみ実装されています。`sim` と `obs` のデータと次元には単位を指定する必要があります。経度と緯度の単位は度である必要があります。リサンプリングは、`obs` を `sim` にリサンプリングすることによって自動的に行われます。

パラメータ `mask` は `OutputVar` をマスクする関数です。[`apply_landmask`](@ref) および [`apply_oceanmask`](@ref) を参照してください。

他にも [`bias`](@ref)、[`squared_error`](@ref)、[`global_mse`](@ref)、[`global_rmse`](@ref) を参照してください。
