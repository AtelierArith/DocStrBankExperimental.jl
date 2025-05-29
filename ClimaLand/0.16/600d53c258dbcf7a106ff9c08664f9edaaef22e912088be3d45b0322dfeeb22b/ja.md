```
PrescribedPrecipitation{FT, LP} <: AbstractAtmosphericDrivers{FT}
```

降水ドライバーを保持するためのコンテナで、降水のみを必要とするモデル（RichardsModel）に使用されます。

  * `liquid_precip`: 時間の関数としての降水（m/s）：定義上正の値
