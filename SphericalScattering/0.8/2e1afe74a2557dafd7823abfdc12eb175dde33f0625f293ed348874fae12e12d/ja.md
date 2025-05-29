```
scatteredfield(sphere::LayeredSpherePEC, excitation::UniformField{FC,FT,FR}, point, quantity::ScalarPotential; parameter::Parameter=Parameter())
```

PECコアを持つ層状誘電体球体によって散乱されるスカラー電位を計算します。与えられた方向に偏光した入射均一場を使用して、`Sihvola and Lindell, 1988, Transmission line analogy for calculating the effective permittivity of mixtures with spherical multilayer scatterers`に基づいています。

`Sihvola and Lindell`とは対照的に、シェルの半径はドキュメントに示されているように内側から外側に向かって順序付けられています。

点と返される場はデカルト座標系で表されます。
