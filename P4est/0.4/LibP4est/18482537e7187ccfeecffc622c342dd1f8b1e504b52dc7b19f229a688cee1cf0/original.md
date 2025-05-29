```
p8est_find_edge_transform(connectivity, itree, iedge, ei)
```

Fills an array with information about edge neighbors.

### Parameters

  * `itree`:[in] The number of the originating tree.
  * `iedge`:[in] The number of the originating edge.
  * `ei`:[in,out] A `p8est_edge_info_t` structure with initialized array.

### Prototype

```c
void p8est_find_edge_transform (p8est_connectivity_t * connectivity, p4est_topidx_t itree, int iedge, p8est_edge_info_t * ei);
```
