```
t8_cmesh_register_geometry(cmesh, geometry)
```

Register a geometry in the cmesh. The cmesh takes ownership of the geometry.

If no geometry is registered and cmesh is modified from another cmesh then the other cmesh's geometries are used.

!!! note
    If you need to use t8*cmesh*bcast, then all geometries must be registered *after* the bcast operation, not before.


# Arguments

  * `cmesh`:[in,out] The cmesh.
  * `geometry`:[in] The geometry to register.

### Prototype

```c
void t8_cmesh_register_geometry (t8_cmesh_t cmesh, t8_geometry_c *geometry);
```
