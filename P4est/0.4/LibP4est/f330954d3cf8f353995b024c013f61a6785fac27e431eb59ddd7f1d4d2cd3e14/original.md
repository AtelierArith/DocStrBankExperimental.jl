```
sc_hash_destroy_null(phash)
```

Destroy a hash table and set its pointer to NULL. Destruction is done using sc*hash*destroy.

### Parameters

  * `phash`:[in,out] Address of pointer to hash table. On output, pointer is NULLed.

### Prototype

```c
void sc_hash_destroy_null (sc_hash_t ** phash);
```
