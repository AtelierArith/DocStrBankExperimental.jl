```
wnsumd(window)
```

ダブル精度ウィンドウの内容を要約します。

### 引数

  * `window`: 要約されるウィンドウ

### 出力

次の要素からなるタプルを返します：

  * `meas`: ウィンドウ内の区間の合計測定値
  * `avg`: 平均測定値
  * `stddev`: 標準偏差
  * `shortest`: 最短区間の位置
  * `longest`: 最長区間の位置

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/wnsumd_c.html)
