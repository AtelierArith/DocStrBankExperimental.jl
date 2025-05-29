```
etcal(et, lenout=128)
```

J2000のエポックからの秒数で測定されたエフェメリスエポックを、うるう秒のない正式なカレンダー文字列形式に変換します。

### 引数

  * `et`: J2000からの秒数で測定されたエフェメリス時間
  * `lenout`: 出力文字列の長さ（デフォルト: 128）

### 出力

`et`の標準カレンダー表現を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/etcal_c.html)
