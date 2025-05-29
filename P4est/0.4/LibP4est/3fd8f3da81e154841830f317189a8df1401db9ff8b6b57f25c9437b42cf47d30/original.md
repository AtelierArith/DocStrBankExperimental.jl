```
p4est_connectivity_complete(conn)
```

Internally connect a connectivity based on tree_to_vertex information. Periodicity that is not inherent in the list of vertices will be lost.

### Parameters

  * `conn`:[in,out] The connectivity needs to have proper vertices and tree_to_vertex fields. The tree_to_tree and tree_to_face fields must be allocated and satisfy [`p4est_connectivity_is_valid`](@ref) (conn) but will be overwritten. The corner fields will be freed and allocated anew.

### Prototype

```c
void p4est_connectivity_complete (p4est_connectivity_t * conn);
```
