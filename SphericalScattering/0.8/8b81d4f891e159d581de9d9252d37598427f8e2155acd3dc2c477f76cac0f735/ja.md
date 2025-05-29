```
scatteredfield(sphere::PECSphere, excitation::Dipole, point, quantity::ElectricField; parameter::Parameter=Parameter())
```

PEC球体によって散乱される電場を計算します。ダイポールはz軸に沿ってz0に配置されています。

点と返される場はデカルト座標系で表されます。
