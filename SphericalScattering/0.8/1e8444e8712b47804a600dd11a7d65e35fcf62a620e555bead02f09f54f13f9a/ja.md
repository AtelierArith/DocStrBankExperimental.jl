```
scatteredfield(sphere::PECSphere, excitation::RingCurrent, point, quantity::ElectricField; parameter::Parameter=Parameter())
```

PEC球体によって散乱される電場を計算します。リング電流はz軸に沿って配置されています。

点と返される電場はデカルト座標系で表されます。
