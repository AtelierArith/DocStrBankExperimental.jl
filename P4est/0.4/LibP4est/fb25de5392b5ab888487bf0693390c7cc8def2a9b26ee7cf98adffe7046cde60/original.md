```
p8est_connectivity_face_neighbor_corner_set(c, f, nf, set)
```

Transform a corner across one of the adjacent faces into a neighbor tree. It expects a face permutation index that has been precomputed.

### Parameters

  * `c`:[in] A corner number in 0..7.
  * `f`:[in] A face number that touches the corner *c*.
  * `nf`:[in] A neighbor face that is on the other side of .
  * `set`:[in] A value from *p8est*face*permutation_sets* that is obtained using *f*, *nf*, and a valid orientation: ref = p8est_face_permutation_refs[f][nf]; set = p8est_face_permutation_sets[ref][orientation];

### Returns

The corner number in 0..7 seen from the other face.

### Prototype

```c
int p8est_connectivity_face_neighbor_corner_set (int c, int f, int nf, int set);
```
