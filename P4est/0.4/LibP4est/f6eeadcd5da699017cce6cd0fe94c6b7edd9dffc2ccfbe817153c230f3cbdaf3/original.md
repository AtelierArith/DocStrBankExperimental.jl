```
p8est_connectivity_face_neighbor_edge(e, f, nf, o)
```

Transform an edge across one of the adjacent faces into a neighbor tree. This version expects the neighbor face and orientation separately.

`.`

### Parameters

  * `e`:[in] A edge number in 0..11.
  * `f`:[in] A face 0..5 that touches the edge *e*.
  * `nf`:[in] A neighbor face that is on the other side of .
  * `o`:[in] The orientation between tree boundary faces *f* and

### Returns

The edge's number seen from the neighbor.

### Prototype

```c
int p8est_connectivity_face_neighbor_edge (int e, int f, int nf, int o);
```
