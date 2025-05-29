```
spkcov!(cover, spk, idcode)
```

指定されたSPKファイル内の指定された軌道要素オブジェクトのカバレッジウィンドウを見つけます。

### 引数

  * `cover`: `spk`内の`idcode`に対するカバレッジを示すウィンドウ
  * `spk`: SPKファイルの名前
  * `idcode`: 軌道要素オブジェクトのIDコード

### 出力

拡張されたカバレッジウィンドウを返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkcov_c.html)
