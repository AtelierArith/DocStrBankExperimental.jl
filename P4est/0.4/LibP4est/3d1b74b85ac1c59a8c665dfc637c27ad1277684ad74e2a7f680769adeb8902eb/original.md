```
sc_hash_array_insert_unique(hash_array, v, position)
```

Insert an object into a hash array if it is not contained already. The object is not copied into the array. Use the return value for that. New objects are guaranteed to be added at the end of the array.

### Parameters

  * `v`:[in] A pointer to the object. Used for search only.
  * `position`:[out] If position != NULL, *position is set to the array position of the already contained, or if not present, the new object.

### Returns

Returns NULL if the object is already contained. Otherwise returns its new address in the array.

### Prototype

```c
void *sc_hash_array_insert_unique (sc_hash_array_t * hash_array, void *v, size_t *position);
```
