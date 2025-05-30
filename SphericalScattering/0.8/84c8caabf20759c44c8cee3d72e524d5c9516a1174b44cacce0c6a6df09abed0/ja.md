```
scatteredfield(sphere::PECSphere, excitation::UniformField, point, quantity::ElectricField; parameter::Parameter=Parameter())
```

PEC球体によって散乱される電場を計算します。入射する均一な電場は、指定された方向に偏光しています。

点と返される電場は直交座標系で表されます。
