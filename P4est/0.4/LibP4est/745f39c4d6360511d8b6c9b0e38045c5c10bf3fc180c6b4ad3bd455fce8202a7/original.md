```
sc_mstamp_reset(mst)
```

Free all memory in a stamp structure and all items previously returned.

### Parameters

  * `Properly`:[in,out] initialized stamp container. On output, the structure is undefined.

### Prototype

```c
void sc_mstamp_reset (sc_mstamp_t * mst);
```
