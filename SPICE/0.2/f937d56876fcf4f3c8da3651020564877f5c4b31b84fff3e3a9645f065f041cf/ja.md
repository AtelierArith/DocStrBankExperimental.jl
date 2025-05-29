```
fovray(inst, raydir, rframe, abcorr, observer, et)
```

指定された時刻において、指定された機器の視野（FOV）内に特定の光線があるかどうかを判断します。

### 引数

  * `inst`: 機器の名前またはIDコードの文字列
  * `raydir`: 光線の方向ベクトル
  * `rframe`: 対象天体の体固定、体中心フレーム
  * `abcorr`: 異常補正フラグ
  * `observer`: 観測者の名前またはIDコードの文字列
  * `et`: 観測の時刻（J2000からの秒数）

### 出力

光線が可視であれば `true` を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/fovray_c.html)
