```
p4est_qcoord_to_vertex(connectivity, treeid, x, y, vxyz)
```

四分木座標を木の頂点によって張られた空間に変換します。

### パラメータ

  * `connectivity`:[in] 接続情報は頂点を提供する必要があります。
  * `treeid`:[in] x, y を含む木を識別します。
  * `x,`:[in] y は treeid に対する四分木座標です。
  * `vxyz`:[out] 頂点空間における変換された座標です。

### プロトタイプ

```c
void p4est_qcoord_to_vertex (p4est_connectivity_t * connectivity, p4est_topidx_t treeid, p4est_qcoord_t x, p4est_qcoord_t y, double vxyz[3]);
```
