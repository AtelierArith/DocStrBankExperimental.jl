```
npelpt(point, ellips)
```

指定された点に最も近い楕円上の点を見つけ、楕円とその点との距離を求めます。

### 引数

  * `point`: 楕円までの距離を求める点
  * `ellips`: SPICE 楕円

### 出力

`pnear` と `dist` からなるタプルを返します。

  * `pnear`: 入力点に最も近い楕円上の点
  * `dist`: 入力点から楕円までの距離

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/npelpt_c.html)
