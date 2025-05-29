```
p4est_connectivity_face_neighbor_face_corner(fc, f, nf, o)
```

Transform a face corner across one of the adjacent faces into a neighbor tree. This version expects the neighbor face and orientation separately.

`.`

### Parameters

  * `fc`:[in] A face corner number in 0..1.
  * `f`:[in] A face that the face corner number *fc* is relative to.
  * `nf`:[in] A neighbor face that is on the other side of .
  * `o`:[in] The orientation between tree boundary faces *f* and

### Returns

The face corner number relative to the neighbor's face.

### Prototype

```c
int p4est_connectivity_face_neighbor_face_corner (int fc, int f, int nf, int o);
```
