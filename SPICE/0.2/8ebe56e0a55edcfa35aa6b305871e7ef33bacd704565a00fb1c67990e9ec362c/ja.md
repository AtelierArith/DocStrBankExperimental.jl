```
sce2c(sc, et)
```

J2000以降のエフェメリス秒（ET）を連続エンコードされた宇宙船時計（"ticks"）に変換します。非整数のティック値が返される場合があります。

### 引数

  * `sc`: NAIF宇宙船IDコード
  * `et`: エフェメリス時間、J2000以降の秒数

### 出力

宇宙船時計の開始からのティックとしてエンコードされたSCLKを返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/sce2c_c.html)
