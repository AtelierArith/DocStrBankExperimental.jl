```
sct2e(sc, sclkdp)
```

エンコードされた宇宙船時計（"ティック"）をJ2000（ET）以降のエフェメリス秒に変換します。

### 引数

  * `sc`: 宇宙船のためのNAIF整数コード
  * `sclkdp`: 宇宙船時計の開始からのティックとしてエンコードされたSCLK。

### 出力

J2000以降のエフェメリスタイム秒を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/sct2e_c.html)
