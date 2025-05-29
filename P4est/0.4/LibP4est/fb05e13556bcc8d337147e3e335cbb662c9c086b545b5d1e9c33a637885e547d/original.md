```
sc_mstamp_alloc(mst)
```

Return a new item. The memory returned will stay legal until container is destroyed or truncated.

### Parameters

  * `Properly`:[in,out] initialized stamp container.

### Returns

Pointer to an item ready to use. Legal until sc*stamp*destroy or sc*stamp*truncate is called on mst.

### Prototype

```c
void *sc_mstamp_alloc (sc_mstamp_t * mst);
```
