```
p8est_connectivity_set_attr(conn, bytes_per_tree)
```

Allocate or free the attribute fields in a connectivity.

### Parameters

  * `conn`:[in,out] The conn->*_to_attr fields must either be NULL or previously be allocated by this function.
  * `bytes_per_tree`:[in] If 0, tree_to_attr is freed (being NULL is ok). If positive, requested space is allocated.

### Prototype

```c
void p8est_connectivity_set_attr (p8est_connectivity_t * conn, size_t bytes_per_tree);
```
