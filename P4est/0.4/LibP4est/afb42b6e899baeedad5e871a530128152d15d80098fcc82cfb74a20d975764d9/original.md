```
p8est_connectivity_face_neighbor_corner(c, f, nf, o)
```

Transform a corner across one of the adjacent faces into a neighbor tree. This version expects the neighbor face and orientation separately.

`.`

### Parameters

  * `c`:[in] A corner number in 0..7.
  * `f`:[in] A face number that touches the corner *c*.
  * `nf`:[in] A neighbor face that is on the other side of .
  * `o`:[in] The orientation between tree boundary faces *f* and

### Returns

The number of the corner seen from the neighbor tree.

### Prototype

```c
int p8est_connectivity_face_neighbor_corner (int c, int f, int nf, int o);
```
