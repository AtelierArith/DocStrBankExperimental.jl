```
scatteredfield(sphere::DielectricSphereThinImpedanceLayer, excitation::UniformField, point, quantity::ElectricField; parameter::Parameter=Parameter())
```

薄いコーティングを持つ誘電体球体によって散乱される電場を計算します。このコーティング内の変位場は放射方向のみに存在すると仮定します。与えられた方向に偏光を持つ入射均一場を仮定します。

点と返される場はデカルト座標系で表されます。
