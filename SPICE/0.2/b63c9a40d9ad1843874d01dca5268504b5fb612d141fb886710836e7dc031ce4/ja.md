```
nplnpt(linept, linedr, point)
```

指定された点に最も近い線上の点を見つけ、2つの点の間の距離を求めます。

### 引数

  * `linept`: 線上の点
  * `linedr`: 線の方向ベクトル
  * `point`: 2つ目の点

### 出力

`pnear` と `dist` からなるタプルを返します。

  * `pnear`: `point` に最も近い線上の点
  * `dist`: `point` と `pnear` の間の距離

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/nplnpt_c.html)

```
