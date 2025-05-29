```
occult(targ1, shape1, frame1, targ2, shape2, frame2, abcorr, obsrvr, et)
```

指定された時刻に観測者から見たときの、1つのターゲットが別のターゲットに対しての隠蔽条件（隠蔽されていない、部分的に隠蔽されているなど）を決定します。

ターゲット天体の表面は、三軸楕円体またはDSKファイルによって提供される地形データで表現される場合があります。

### 引数

  * `targ1`: 最初のターゲットの名前またはID。
  * `shape1`: 最初のターゲットに使用される形状モデルのタイプ。
  * `frame1`: 最初の天体の体固定、体中心フレーム。
  * `targ2`: 2番目のターゲットの名前またはID。
  * `shape2`: 2番目のターゲットに使用される形状モデルのタイプ。
  * `frame2`: 2番目の天体の体固定、体中心フレーム。
  * `abcorr`: 異常補正フラグ。
  * `obsrvr`: 観測者の名前またはID。
  * `et`: 観測の時刻（J2000からの秒数）。

### 出力

隠蔽識別コードを返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/occult_c.html)
