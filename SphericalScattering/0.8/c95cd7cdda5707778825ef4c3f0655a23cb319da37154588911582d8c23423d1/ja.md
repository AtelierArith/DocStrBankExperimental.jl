```
scatteredfield(sphere::Sphere, excitation::PlaneWave, point, quantity::Field; parameter::Parameter=Parameter())
```

PECまたは誘電体球体によって散乱される電場を計算します。入射平面波は+z方向に進行し、Eフィールドの偏光はx方向です。

点と返されるフィールドはデカルト座標系で表されます。
