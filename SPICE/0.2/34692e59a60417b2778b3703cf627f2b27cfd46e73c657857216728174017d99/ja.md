```
rotvec(v1, angle, iaxis)
```

ベクトルを、軸 `iaxis` の周りに `angle` ラジアン回転した新しい座標系に変換します。この変換は、指定された軸の周りに `v1` を `-angle` ラジアン回転させます。

### 引数

  * `v1`: 座標系を回転させるベクトル
  * `angle`: ラジアンでの回転角
  * `iaxis`: 回転軸 (X=1, Y=2, Z=3)

### 出力

新しい座標系で表現された結果のベクトルを返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/rotvec_c.html)
