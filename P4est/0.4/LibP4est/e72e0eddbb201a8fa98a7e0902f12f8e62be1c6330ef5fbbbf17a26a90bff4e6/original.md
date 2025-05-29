```
p6est_qcoord_to_vertex(connectivity, treeid, x, y, z, vxyz)
```

Transform a quadrant coordinate into the space spanned by tree vertices.

### Parameters

  * `connectivity`:[in] Connectivity must provide the vertices.
  * `treeid`:[in] Identify the tree that contains x, y.
  * `x,`:[in] y Quadrant coordinates relative to treeid.
  * `vxy`:[out] Transformed coordinates in vertex space.

### Prototype

```c
void p6est_qcoord_to_vertex (p6est_connectivity_t * connectivity, p4est_topidx_t treeid, p4est_qcoord_t x, p4est_qcoord_t y, p4est_qcoord_t z, double vxyz[3]);
```
