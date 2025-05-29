```
p4est_qcoord_to_vertex(connectivity, treeid, x, y, vxyz)
```

Transform a quadrant coordinate into the space spanned by tree vertices.

### Parameters

  * `connectivity`:[in] Connectivity must provide the vertices.
  * `treeid`:[in] Identify the tree that contains x, y.
  * `x,`:[in] y Quadrant coordinates relative to treeid.
  * `vxyz`:[out] Transformed coordinates in vertex space.

### Prototype

```c
void p4est_qcoord_to_vertex (p4est_connectivity_t * connectivity, p4est_topidx_t treeid, p4est_qcoord_t x, p4est_qcoord_t y, double vxyz[3]);
```
