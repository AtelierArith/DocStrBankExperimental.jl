```
unitim(epoch, insys, outsys)
```

異なる一様スケールから別の一様スケールに時間を変換します。

### 引数

  * `epoch`: 変換されるエポック
  * `insys`: 入力エポックに関連付けられた時間スケール
  * `outsys`: 関数値に関連付けられた時間スケール

一様時間スケールは次のとおりです：

  * `:TAI`
  * `:TDT`
  * `:TDB`
  * `:ET`
  * `:JED`
  * `:JDTDB`
  * `:JDTDT`

### 出力

`insys` 時間スケールの `epoch` に相当する `outsys` で指定されたシステムの時間を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/unitim_c.html)
