```
p4est_ghost_expand_by_lnodes(p4est_, lnodes, ghost)
```

Expand the ghost layer as in [`p4est_ghost_expand`](@ref)(), but use node support to define adjacency instead of geometric adjacency.

### Parameters

  * `p4est`:[in] The forest from which the ghost layer was generated.
  * `lnodes`:[in] The nodes to support.
  * `ghost`:[in,out] The ghost layer to be expanded.

### Prototype

```c
void p4est_ghost_expand_by_lnodes (p4est_t * p4est, p4est_lnodes_t * lnodes, p4est_ghost_t * ghost);
```
