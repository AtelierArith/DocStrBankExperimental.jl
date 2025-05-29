```
ClimaLand.total_liq_water_vol_per_area!(
    surface_field,
    model::SnowModel,
    Y,
    p,
    t,
```

)

`SnowModel`の単位面積あたりの総液体水量の値で`surface_field`をインプレースで更新する関数です。

これはすでにSの定義における雪の面積比を考慮しており、雪に存在する液体と凍結水の両方を考慮しています。雪水等価は、すべての雪が溶けた場合に雪に存在する総液体水量を単位面積あたりで示しています。
