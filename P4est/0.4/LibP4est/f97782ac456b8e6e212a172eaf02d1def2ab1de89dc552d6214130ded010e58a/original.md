```
p8est_connectivity_new_shell()
```

Create a connectivity structure that builds a spherical shell. It is made up of six connected parts [-1,1]x[-1,1]x[1,2]. This connectivity reuses vertices and relies on a geometry transformation. It is thus not suitable for [`p8est_connectivity_complete`](@ref).

### Prototype

```c
p8est_connectivity_t *p8est_connectivity_new_shell (void);
```
