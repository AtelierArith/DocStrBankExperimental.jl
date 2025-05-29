```
ClimaLand.total_energy_per_area!(
    surface_field,
    model::BigLeafEnergyModel,
    Y,
    p,
    t,
```

)

ビッグリーフモデルのエネルギーの値で `surface_field` をインプレースで更新する関数です。

これは、キャノピーとステムコンポーネントが最大で1つだけ存在し、それらの面積インデックスが統合面積インデックス（高さにおいて）を指すことを前提としています - レイヤーごとの値ではありません。
