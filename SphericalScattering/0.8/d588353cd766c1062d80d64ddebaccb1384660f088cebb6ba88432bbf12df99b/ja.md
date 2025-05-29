```
scatteredfield(sphere::DielectricSphere, excitation::UniformField, point, quantity::ScalarPotential; parameter::Parameter=Parameter())
```

誘電体球体によって散乱されるスカラー電位を計算します。入射する均一な電場は、指定された方向に偏光しています。

点と返される場は直交座標系で表されます。
