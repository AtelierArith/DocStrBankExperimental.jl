```
p8est_connectivity_new_torus(nSegments)
```

Create a connectivity structure that builds a revolution torus.

This connectivity reuses vertices and relies on a geometry transformation. It is thus not suitable for [`p8est_connectivity_complete`](@ref).

This connectivity reuses ideas from disk2d connectivity. More precisely the torus is divided into segments arround the revolution axis, each segments is made of 5 trees (à la disk2d). The total number of trees if 5 times the number of segments.

This connectivity is meant to be used with p8est*geometry*new_torus

### Parameters

  * `nSegments`:[in] number of trees along the great circle

### Prototype

```c
p8est_connectivity_t *p8est_connectivity_new_torus (int nSegments);
```
