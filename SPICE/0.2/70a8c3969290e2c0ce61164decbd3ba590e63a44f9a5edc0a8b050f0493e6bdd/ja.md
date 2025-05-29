```
pckcov!(cover, pck, idcode)
```

指定されたバイナリPCKファイル内の指定された参照フレームのカバレッジウィンドウを見つけます。

### 引数

  * `cover`: 初期化されたウィンドウ `SpiceDoubleCell`
  * `pck`: PCKファイルのパス
  * `idcode`: PCK参照フレームのクラスIDコード

### 出力

`idcode`に対する`pck`内のカバレッジを含む`cover`を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/pckcov_c.html)
