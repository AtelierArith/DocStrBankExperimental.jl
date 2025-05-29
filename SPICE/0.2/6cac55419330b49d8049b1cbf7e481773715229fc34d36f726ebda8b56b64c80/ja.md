```
nearpt(positn, a, b, c)
```

このルーチンは、指定された位置に最も近い楕円体の表面上の点を特定します。また、楕円体の上の位置の高度も返します。

### 引数

  * `positn`: 固定された体のフレーム内の点の位置
  * `a`: x軸に平行な半軸の長さ
  * `b`: y軸に平行な半軸の長さ
  * `c`: z軸に平行な半軸の長さ

### 出力

`npoint`と`alt`からなるタプルを返します。

  * `npoint`: `positn`に最も近い楕円体上の点
  * `alt`: 楕円体の上の`positn`の高度

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/nearpt_c.html)
