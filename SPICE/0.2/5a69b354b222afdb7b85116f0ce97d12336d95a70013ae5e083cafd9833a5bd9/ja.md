```
pxfrm2(from, to, etfrom, etto)
```

指定されたエポックでの1つの指定されたフレームから、別の指定されたエポックでの別の指定されたフレームへの位置ベクトルを変換する3×3行列を返します。

### 引数

  * `from`: 変換元のフレームの名前
  * `to`: 変換先のフレームの名前
  * `etfrom`: `from`フレームの評価時間
  * `etto`: `to`フレームの評価時間

### 出力

フレーム`from`からフレーム`to`への位置変換行列を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/pxfrm2_c.html)
