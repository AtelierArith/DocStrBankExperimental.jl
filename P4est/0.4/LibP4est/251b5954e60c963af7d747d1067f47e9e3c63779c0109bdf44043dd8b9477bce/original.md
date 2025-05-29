```
p8est_expand_face_transform(iface, nface, ftransform)
```

Fill an array with the axis combination of a face neighbor transform.

### Parameters

  * `iface`:[in] The number of the originating face.
  * `nface`:[in] Encoded as nface = r * 6 + nf, where nf = 0..5 is the neigbbor's connecting face number and r = 0..3 is the relative orientation to the neighbor's face. This encoding matches [`p8est_connectivity_t`](@ref).
  * `ftransform`:[out] This array holds 9 integers. [0]..[2] The coordinate axis sequence of the origin face, the first two referring to the tangentials and the third to the normal. A permutation of (0, 1, 2). [3]..[5] The coordinate axis sequence of the target face. [6]..[8] Edge reversal flags for tangential axes (boolean); face code in [0, 3] for the normal coordinate q: 0: q' = -q 1: q' = q + 1 2: q' = q - 1 3: q' = 2 - q

### Prototype

```c
void p8est_expand_face_transform (int iface, int nface, int ftransform[]);
```
