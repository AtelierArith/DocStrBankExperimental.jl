```
sc_mstamp_init(mst, stamp_unit, elem_size)
```

Initialize a memory stamp container. We provide allocation of fixed-size memory items without allocating new memory in every request. Instead we block the allocations in what we call a stamp of multiple items. Even if no allocations are done, the container's internal memory must be freed eventually by sc*mstamp*reset.

### Parameters

  * `mst`:[in,out] Legal pointer to a stamp structure.
  * `stamp_unit`:[in] Size of each memory block that we allocate. If it is larger than the element size, we may place more than one element in it. Passing 0 is legal and forces stamps that hold one item each.
  * `elem_size`:[in] Size of each item. Passing 0 is legal. In that case, sc*mstamp*alloc returns NULL.

### Prototype

```c
void sc_mstamp_init (sc_mstamp_t * mst, size_t stamp_unit, size_t elem_size);
```
