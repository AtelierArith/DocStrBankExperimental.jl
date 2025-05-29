```
p8est_connectivity_edge_neighbor_corner(c, e, ne, o)
```

Transform a corner across one of the adjacent edges into a neighbor tree. This version expects the neighbor edge and orientation separately.

### Parameters

  * `c`:[in] A corner number in 0..7.
  * `e`:[in] An edge 0..11 that touches the corner *c*.
  * `ne`:[in] A neighbor edge that is on the other side of *.*
  * `o`:[in] The orientation between tree boundary edges *e* and *.*

### Returns

Corner number seen from the neighbor.

### Prototype

```c
int p8est_connectivity_edge_neighbor_corner (int c, int e, int ne, int o);
```
