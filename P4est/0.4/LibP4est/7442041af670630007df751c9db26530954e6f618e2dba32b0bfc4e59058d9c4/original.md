```
sc_hash_remove(hash, v, found)
```

Remove an object from a hash table.

### Parameters

  * `v`:[in] The object to be removed.
  * `found`:[out] If found != NULL, *found is set to the object that is removed if that exists.

### Returns

Returns true if object is found, false if is not contained.

### Prototype

```c
int sc_hash_remove (sc_hash_t * hash, void *v, void **found);
```
