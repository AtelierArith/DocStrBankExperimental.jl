```
p8est_connectivity_new_twotrees(l_face, r_face, orientation)
```

Create a connectivity structure for two trees being rotated w.r.t. each other in a user-defined way.

### Parameters

  * `l_face`:[in] index of left face
  * `r_face`:[in] index of right face
  * `orientation`:[in] orientation of trees w.r.t. each other

### Prototype

```c
p8est_connectivity_t *p8est_connectivity_new_twotrees (int l_face, int r_face, int orientation);
```
