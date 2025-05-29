```
scatteredfield(sphere::LayeredSphere, excitation::UniformField, point, quantity::ElectricField; parameter::Parameter=Parameter())
```

層状誘電体球体によって散乱される電場を計算します。入射する均一な電場は、与えられた方向に偏光しています。これは「Sihvola and Lindell, 1988, Transmission line analogy for calculating the effective permittivity of mixtures with spherical multilayer scatterers」に基づいています。

`Sihvola and Lindell`とは対照的に、シェルの半径はドキュメントに示されているように内側から外側に向かって順序付けられています。

点と返される電場はデカルト座標系で表されます。
