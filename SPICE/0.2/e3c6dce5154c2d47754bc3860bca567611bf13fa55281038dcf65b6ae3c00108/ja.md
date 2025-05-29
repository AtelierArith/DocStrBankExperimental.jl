```
fovtrg(inst, target, tshape, tframe, abcorr, obsrvr, et)
```

指定されたエフェメリスオブジェクトが、指定された時刻において指定された機器の視野（FOV）内にあるかどうかを判断します。

### 引数

  * `inst`: 機器の名前またはIDコードの文字列。
  * `target`: 対象の名前またはIDコードの文字列。
  * `tshape`: 対象に使用される形状モデルのタイプ。
  * `tframe`: 対象天体の体固定、体中心フレーム。
  * `abcorr`: 異常補正フラグ。
  * `obsrvr`: 観測者の名前またはIDコードの文字列。
  * `et`: 観測の時刻（J2000からの秒数）。

### 出力

オブジェクトが可視であれば`true`を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/fovtrg_c.html)
