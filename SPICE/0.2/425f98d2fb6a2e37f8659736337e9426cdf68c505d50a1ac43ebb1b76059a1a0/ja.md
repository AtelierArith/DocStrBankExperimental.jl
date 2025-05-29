```
twovec(axdef, indexa, plndef, indexp)
```

指定された軸として与えられたベクトルを持ち、指定された座標平面内にある第二の与えられたベクトルを持つ右手系への変換を見つけます。

### 引数

  * `axdef`: 主軸を定義するベクトル
  * `indexa`: axdefの主軸番号 (X=1, Y=2, Z=3)
  * `plndef`: (axdefと共に) 主平面を定義するベクトル
  * `indexp`: 主平面の第二軸番号 (indexaと共に)

### 出力

出力回転行列を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/twovec_c.html)
