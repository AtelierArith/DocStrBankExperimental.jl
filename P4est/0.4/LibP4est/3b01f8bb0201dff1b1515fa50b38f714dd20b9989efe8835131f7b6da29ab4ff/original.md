```
sc_mstamp_truncate(mst)
```

Free all memory in a stamp structure and initialize it anew. Equivalent to calling sc*mstamp*reset followed by sc*mstamp*init with the same stamp_unit and elem_size.

### Parameters

  * `Properly`:[in,out] initialized stamp container. On output, its elements have been freed and it is ready for further use.

### Prototype

```c
void sc_mstamp_truncate (sc_mstamp_t * mst);
```
