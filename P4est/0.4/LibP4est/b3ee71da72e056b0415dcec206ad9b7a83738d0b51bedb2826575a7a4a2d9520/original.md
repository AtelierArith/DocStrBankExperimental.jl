```
p8est_ghost_expand_by_lnodes(p4est_, lnodes, ghost)
```

Expand the ghost layer as in [`p8est_ghost_expand`](@ref)(), but use node support to define adjacency instead of geometric adjacency.

### Parameters

  * `p8est`:[in] The forest from which the ghost layer was generated.
  * `lnodes`:[in] The nodes to support.
  * `ghost`:[in,out] The ghost layer to be expanded.

### Prototype

```c
void p8est_ghost_expand_by_lnodes (p8est_t * p4est, p8est_lnodes_t * lnodes, p8est_ghost_t * ghost);
```
