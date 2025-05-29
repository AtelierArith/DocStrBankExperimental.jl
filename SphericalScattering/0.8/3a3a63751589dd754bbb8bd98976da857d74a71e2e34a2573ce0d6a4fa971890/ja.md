```
scatteredfield(sphere::PECSphere, excitation::SphericalModeTE, point, quantity::ElectricField; parameter::Parameter=Parameter())
```

PEC球体によって散乱される電場を計算します。これは、原点に向かって進む球面モードによって励起されます。

点と返される場はデカルト座標系で表されます。
