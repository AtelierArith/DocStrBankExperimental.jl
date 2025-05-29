```
p8est_lnodes_share_all(node_data, lnodes)
```

Equivalend to calling [`p8est_lnodes_share_all_end`](@ref) directly after [`p8est_lnodes_share_all_begin`](@ref). Use if there is no local work that can be done to mask the communication cost.

### Returns

A fully initialized buffer that contains the received data. After processing this data, the buffer must be freed with [`p8est_lnodes_buffer_destroy`](@ref).

### Prototype

```c
p8est_lnodes_buffer_t *p8est_lnodes_share_all (sc_array_t * node_data, p8est_lnodes_t * lnodes);
```
