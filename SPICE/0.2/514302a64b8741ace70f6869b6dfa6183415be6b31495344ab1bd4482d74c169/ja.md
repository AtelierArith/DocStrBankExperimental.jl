```
pltnp(point, v1, v2, v3)
```

与えられた点に最も近い三角形プレート上の点を見つけます。

### 引数

  * `point`: 3次元空間の点。
  * `v1`, `v2`, `v3`: 三角形プレートの頂点

### 出力

次の要素からなるタプルを返します。

  * `pnear`: `point` に最も近いプレート上の点
  * `dist`: `pnear` と `point` の間の距離

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/pltnp_c.html)
