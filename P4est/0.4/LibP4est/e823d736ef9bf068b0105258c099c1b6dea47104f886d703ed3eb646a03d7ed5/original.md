```
sc_hash_lookup(hash, v, found)
```

Check if an object is contained in the hash table.

### Parameters

  * `v`:[in] The object to be looked up.
  * `found`:[out] If found != NULL, *found is set to the address of the pointer to the already contained object if the object is found. You can assign to **found to override.

### Returns

Returns true if object is found, false otherwise.

### Prototype

```c
int sc_hash_lookup (sc_hash_t * hash, void *v, void ***found);
```
