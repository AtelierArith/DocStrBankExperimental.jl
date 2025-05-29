```
t8_mesh_get_element_class(mesh, locid)
```

# Arguments

  * `locid`:[in] The local number can specify a point of any dimension that is locally relevant. The points are ordered in reverse to the element classes in t8*eclass*t. The local index is cumulative in this order.

### Prototype

```c
t8_locidx_t t8_mesh_get_element_class (t8_mesh_t *mesh, t8_locidx_t locid);
```
