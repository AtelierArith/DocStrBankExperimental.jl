```
sce2t(sc, et)
```

J2000以降のエフェメリス秒（ET）を整数エンコードされた宇宙船クロック（"ticks"）に変換します。分数ティックへの変換（Cカーネル生成に必要）は、ルーチン[`sce2c`](@ref)を参照してください。

### 引数

  * `sc`: NAIF宇宙船IDコード
  * `et`: エフェメリス時間、J2000以降の秒数

### 出力

宇宙船クロックの開始からのティックとしてエンコードされたSCLKを返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/sce2c_t.html)
