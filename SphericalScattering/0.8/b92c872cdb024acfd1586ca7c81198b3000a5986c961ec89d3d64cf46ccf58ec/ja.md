```
scatteredfield(sphere::PECSphere, excitation::FitzgeraldDipole, quantity::FarField; parameter::Parameter=Parameter())
```

PEC球体によって散乱される電気的遠方場を計算します。ダイポールはz軸に沿ってz0に配置されています。

点と返される場はデカルト座標系で表されます。
