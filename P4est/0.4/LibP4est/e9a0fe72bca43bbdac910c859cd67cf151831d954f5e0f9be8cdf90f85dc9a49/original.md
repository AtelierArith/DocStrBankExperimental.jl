```
p4est_lnodes_share_owned(node_data, lnodes)
```

Equivalent to calling [`p4est_lnodes_share_owned_end`](@ref) directly after [`p4est_lnodes_share_owned_begin`](@ref). Use if there is no local work that can be done to mask the communication cost.

### Prototype

```c
void p4est_lnodes_share_owned (sc_array_t * node_data, p4est_lnodes_t * lnodes);
```
