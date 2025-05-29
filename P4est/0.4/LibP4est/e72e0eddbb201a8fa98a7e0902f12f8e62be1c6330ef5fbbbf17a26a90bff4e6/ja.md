```
p6est_qcoord_to_vertex(connectivity, treeid, x, y, z, vxyz)
```

四分木座標を木の頂点によって張られた空間に変換します。

### パラメータ

  * `connectivity`:[in] 接続情報は頂点を提供する必要があります。
  * `treeid`:[in] x, y を含む木を識別します。
  * `x,`:[in] y 四分木座標は treeid に対して相対的です。
  * `vxy`:[out] 頂点空間における変換後の座標。

### プロトタイプ

```c
void p6est_qcoord_to_vertex (p6est_connectivity_t * connectivity, p4est_topidx_t treeid, p4est_qcoord_t x, p4est_qcoord_t y, p4est_qcoord_t z, double vxyz[3]);
```
