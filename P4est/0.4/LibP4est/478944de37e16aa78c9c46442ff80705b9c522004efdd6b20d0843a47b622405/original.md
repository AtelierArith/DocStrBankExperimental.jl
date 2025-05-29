```
p8est_connectivity_face_neighbor_face_edge(fe, f, nf, o)
```

Transform a face-edge across one of the adjacent faces into a neighbor tree. This version expects the neighbor face and orientation separately.

`.`

### Parameters

  * `fe`:[in] A face edge number in 0..3.
  * `f`:[in] A face number that touches the edge *e*.
  * `nf`:[in] A neighbor face that is on the other side of .
  * `o`:[in] The orientation between tree boundary faces *f* and

### Returns

The face edge number seen from the neighbor tree.

### Prototype

```c
int p8est_connectivity_face_neighbor_face_edge (int fe, int f, int nf, int o);
```
