```
sce2s(sc, et, lenout=128)
```

J2000（ET）からのエフェメリス秒として指定されたエポックを宇宙船時計値（SCLK）の文字列表現に変換します。

### 引数

  * `sc`: NAIF宇宙船識別コード
  * `et`: エフェメリス時間、J2000からの秒数として指定
  * `lenout`: 出力SCLK文字列の最大許容長

### 出力

SCLK文字列を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/sce2s_c.html)
