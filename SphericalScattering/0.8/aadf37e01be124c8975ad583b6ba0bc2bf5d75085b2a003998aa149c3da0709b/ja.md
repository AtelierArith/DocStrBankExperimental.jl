```
scatteredfield(sphere::PECSphere, excitation::MagneticRingCurrent, quantity::FarField; parameter::Parameter=Parameter())
```

PEC球体によって散乱される電気的遠方場を計算します。リング電流はz軸に沿って配置されています。

点と返される場はデカルト座標系にあります。
