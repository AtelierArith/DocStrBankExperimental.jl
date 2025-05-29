```
rotation(ref::GeometryReference; α0=0)
```

`transformation(ref)`を適用したときの角度の変化で、元々`x`軸から`α0`の反時計回りにある直線に対してです。

`rotation(transformation(ref); α0=α0)`と同等です。
