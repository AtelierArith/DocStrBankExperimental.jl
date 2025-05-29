```
lithostatic_pressure!(Plithos::Array, Density::Array, dz::Number; g=9.81)
```

3D密度配列からリソスティック圧力を計算します。垂直方向の間隔`dz`が一定であると仮定します。オプションで、重力加速度`g`を指定できます。
