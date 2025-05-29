```
rotmat(m1, angle, iaxis)
```

行列 `m1` に対して、軸 `iaxis` の周りに `angle` ラジアンの回転を適用します。この回転は座標系を回転させるものと考えられます。

### 引数

  * `m1`: 回転させる行列
  * `angle`: 回転角（ラジアン）
  * `iaxis`: 回転軸（X=1, Y=2, Z=3）

### 出力

結果として得られる回転行列を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/rotmat_c.html)
