```
p8est_find_face_transform(connectivity, itree, iface, ftransform)
```

Fill an array with the axis combination of a face neighbor transform.

### Parameters

  * `itree`:[in] The number of the originating tree.
  * `iface`:[in] The number of the originating tree's face.
  * `ftransform`:[out] This array holds 9 integers. [0]..[2] The coordinate axis sequence of the origin face. [3]..[5] The coordinate axis sequence of the target face. [6]..[8] Edge reverse flag for axes t1, t2; face code for n.

### Returns

The face neighbor tree if it exists, -1 otherwise.

### Prototype

```c
p4est_topidx_t p8est_find_face_transform (p8est_connectivity_t * connectivity, p4est_topidx_t itree, int iface, int ftransform[]);
```
