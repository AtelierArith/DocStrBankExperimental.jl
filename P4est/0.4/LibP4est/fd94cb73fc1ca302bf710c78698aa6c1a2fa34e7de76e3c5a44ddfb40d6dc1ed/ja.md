```
p8est_qcoord_to_vertex(connectivity, treeid, x, y, z, vxyz)
```

四分木座標を木の頂点によって張られた空間に変換します。

### パラメータ

  * `connectivity`:[in] 接続情報は頂点を提供する必要があります。
  * `treeid`:[in] x, y, z を含む木を識別します。
  * `x,`:[in] y, z 四分木座標は treeid に対して相対的です。
  * `vxyz`:[out] 頂点空間における変換された座標。

### プロトタイプ

```c
void p8est_qcoord_to_vertex (p8est_connectivity_t * connectivity, p4est_topidx_t treeid, p4est_qcoord_t x, p4est_qcoord_t y, p4est_qcoord_t z, double vxyz[3]);
```
