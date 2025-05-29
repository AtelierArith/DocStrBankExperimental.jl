```
sc_hash_insert_unique(hash, v, found)
```

Insert an object into a hash table if it is not contained already.

### Parameters

  * `v`:[in] The object to be inserted.
  * `found`:[out] If found != NULL, *found is set to the address of the pointer to the already contained, or if not present, the new object. You can assign to **found to override.

### Returns

Returns true if object is added, false if it is already contained.

### Prototype

```c
int sc_hash_insert_unique (sc_hash_t * hash, void *v, void ***found);
```
