```
ClimaLand.total_liq_water_vol_per_area!(
    surface_field,
    model::PlantHydraulicsModel,
    Y,
    p,
    t,
```

)

植物の水理モデルの総水量で `surface_field` をインプレースで更新する関数です。

これは任意の数のキャノピー層に対して一般的ですが、与えられたLAIとSAIが層ごとのものであると仮定しています。これは、LAIとSAIが高さに対する統合面積指数を指すBigLeafアプローチとは異なります。
