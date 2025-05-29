```
sc_hash_array_lookup(hash_array, v, position)
```

Check if an object is contained in a hash array.

### Parameters

  * `v`:[in] A pointer to the object.
  * `position`:[out] If position != NULL, *position is set to the array position of the already contained object if found.

### Returns

Returns true if object is found, false otherwise.

### Prototype

```c
int sc_hash_array_lookup (sc_hash_array_t * hash_array, void *v, size_t *position);
```
