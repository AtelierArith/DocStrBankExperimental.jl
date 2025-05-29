```
p4est_find_face_transform(connectivity, itree, iface, ftransform)
```

Fill an array with the axis combinations of a tree neighbor transform.

### Parameters

  * `itree`:[in] The number of the originating tree.
  * `iface`:[in] The number of the originating tree's face.
  * `ftransform`:[out] This array holds 9 integers. [0,2] The coordinate axis sequence of the origin face. [3,5] The coordinate axis sequence of the target face. [6,8] Edge reverse flag for axis t; face code for axis n. [1,4,7] 0 (unused for compatibility with 3D).

### Returns

The face neighbor tree if it exists, -1 otherwise.

### Prototype

```c
p4est_topidx_t p4est_find_face_transform (p4est_connectivity_t * connectivity, p4est_topidx_t itree, int iface, int ftransform[]);
```
