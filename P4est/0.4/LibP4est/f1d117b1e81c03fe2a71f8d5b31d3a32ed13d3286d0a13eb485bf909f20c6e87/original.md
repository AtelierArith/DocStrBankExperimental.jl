```
p4est_expand_face_transform(iface, nface, ftransform)
```

Fill an array with the axis combination of a face neighbor transform.

### Parameters

  * `iface`:[in] The number of the originating face.
  * `nface`:[in] Encoded as nface = r * 4 + nf, where nf = 0..3 is the neigbbor's connecting face number and r = 0..1 is the relative orientation to the neighbor's face. This encoding matches [`p4est_connectivity_t`](@ref).
  * `ftransform`:[out] This array holds 9 integers. [0,2] The coordinate axis sequence of the origin face, the first referring to the tangential and the second to the normal. A permutation of (0, 1). [3,5] The coordinate axis sequence of the target face. [6,8] Edge reversal flag for tangential axis (boolean); face code in [0, 3] for the normal coordinate q: 0: q' = -q 1: q' = q + 1 2: q' = q - 1 3: q' = 2 - q [1,4,7] 0 (unused for compatibility with 3D).

### Prototype

```c
void p4est_expand_face_transform (int iface, int nface, int ftransform[]);
```
