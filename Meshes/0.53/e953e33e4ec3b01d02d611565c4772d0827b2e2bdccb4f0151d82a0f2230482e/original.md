```
SimpleTopology(connectivities)
```

A data structure that stores *all* `connectivities` of a mesh.

### Notes

This data structure is sometimes referred to as the "soup of geometries". It does *not* support topological relations and is therefore incompatible with algorithms that rely on neighborhood search. It is still useful for mesh visualization and IO operations.
