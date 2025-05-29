```
rotate(angle, iaxis)
```

指定された軸に関する指定された角度の回転によって生成される3×3回転行列を計算します。この回転は座標系を回転させるものと考えられます。

### 引数

  * `angle`: 回転角（ラジアン）
  * `iaxis`: 回転軸（X=1, Y=2, Z=3）

### 出力

`angle`と`iaxis`に関連する回転行列を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/rotate_c.html)
