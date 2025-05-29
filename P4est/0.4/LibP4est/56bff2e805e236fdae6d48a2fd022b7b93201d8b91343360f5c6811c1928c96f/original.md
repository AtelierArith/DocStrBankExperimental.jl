```
p8est_connectivity_new_sphere()
```

Create a connectivity structure that builds a solid sphere. It is made up of two layers and a cube in the center. This connectivity reuses vertices and relies on a geometry transformation. It is thus not suitable for [`p8est_connectivity_complete`](@ref).

### Prototype

```c
p8est_connectivity_t *p8est_connectivity_new_sphere (void);
```
