```
ClimaLand.total_energy_per_area!(
    surface_field,
    model::AbstractCanopyEnergyModel,
    Y,
    p,
    t,
```

)

キャノピーの一般的なエネルギーモデルに対してエラーを返すデフォルト関数です。

キャノピーエネルギーに対しては2つのモデルのみをサポートしていることに注意してください。`BigLeafEnergyModel`にはこれに特化したメソッドがあり、もう一方は温度が指定されておりエネルギーを保存しません。
