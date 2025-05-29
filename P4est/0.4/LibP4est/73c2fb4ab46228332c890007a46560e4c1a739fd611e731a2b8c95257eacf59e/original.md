```
sc_recycle_array_remove(rec_array, position)
```

Remove an object from the recycle array. It must be valid.

### Parameters

  * `position`:[in] Index into the array for the object to remove.

### Returns

The pointer to the removed object. Will be valid as long as no other function is called on this recycle array.

### Prototype

```c
void *sc_recycle_array_remove (sc_recycle_array_t * rec_array, size_t position);
```
