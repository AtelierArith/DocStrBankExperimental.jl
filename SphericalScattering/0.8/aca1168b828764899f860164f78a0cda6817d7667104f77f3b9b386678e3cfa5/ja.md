```
scatteredfield(sphere::PECSphere, excitation::RingCurrent, quantity::MagneticField; parameter::Parameter=Parameter())
```

PEC球体によって散乱される磁場を計算します。リング電流はz軸に沿って配置されています。

点と返される場はデカルト座標系にあります。
