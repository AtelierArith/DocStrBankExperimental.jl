```
p4est_quadrant_find_owner(p4est_, treeid, face, q)
```

Gets the processor id of a quadrant's owner. The quadrant can lie outside of a tree across faces (and only faces).

!!! warning
    Does not work for tree edge or corner neighbors.


### Parameters

  * `p4est`:[in] The forest in which to search for a quadrant.
  * `treeid`:[in] The tree to which the quadrant belongs.
  * `face`:[in] Supply a face direction if known, or -1 otherwise.
  * `q`:[in] The quadrant that is being searched for.

### Returns

Processor id of the owner or -1 if the quadrant lies outside of the mesh.

### Prototype

```c
int p4est_quadrant_find_owner (p4est_t * p4est, p4est_topidx_t treeid, int face, const p4est_quadrant_t * q);
```
