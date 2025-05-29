```
p8est_revision(p8est_)
```

Return the revision counter of the forest. Not collective, even though the revision value is the same on all ranks. A newly created forest starts with a revision counter of zero. Every refine, coarsen, partition, and balance that actually changes the mesh increases the counter by one. Operations with no effect keep the old value.

### Parameters

  * `p8est`:[in] The forest must be valid.

### Returns

Non-negative number.

### Prototype

```c
long p8est_revision (p8est_t * p8est);
```
