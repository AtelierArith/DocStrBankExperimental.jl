```
ClimaLand.total_energy_per_area!(
    surface_field,
    model::SnowModel,
    Y,
    p,
    t,
```

)

`SnowModel`の単位面積あたりの総エネルギーの値で`surface_field`をインプレースで更新する関数です。

これは、Sの定義における雪の面積比をすでに考慮しています。
