```
p8est_connectivity_edge_neighbor_edge_corner(ec, o)
```

Transform an edge corner across one of the adjacent edges into a neighbor tree.

### Parameters

  * `ec`:[in] An edge corner number in 0..1.
  * `o`:[in] The orientation of a tree boundary edge connection.

### Returns

The edge corner number seen from the other tree.

### Prototype

```c
int p8est_connectivity_edge_neighbor_edge_corner (int ec, int o);
```
