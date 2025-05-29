```
compute_thermal_structure(Temp, X, Y, Z, Phase, s::McKenzie_subducting_slab)
```

`McKenzie_subducting_slab`の温度場を計算します。McKenzie (1969) の解析解 ["Speculations on the consequences and causes of plate motions"] を使用します。この関数は、スラブの底が座標 Z=0 であると仮定しています。内部で関数は座標をシフトします。

パラメータ

=============================

  * `Temp`:  温度配列
  * `X`:    X 配列
  * `Y`:    Y 配列
  * `Z`:    Z 配列
  * `Phase`: フェーズ配列
  * `s`:    `McKenzie_subducting_slab`
