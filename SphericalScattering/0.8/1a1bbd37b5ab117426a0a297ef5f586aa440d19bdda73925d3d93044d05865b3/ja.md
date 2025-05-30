```
scatteredfield(sphere::DielectricSphereThinImpedanceLayer, excitation::UniformField, point, quantity::ScalarPotential; parameter::Parameter=Parameter())
```

薄いコーティングを持つ誘電体球体によって散乱されるスカラー電位を計算します。コーティング内の変位場は放射方向のみに存在すると仮定します。与えられた方向に偏光した入射均一場を仮定します。

点と返される場はデカルト座標系で表されます。
