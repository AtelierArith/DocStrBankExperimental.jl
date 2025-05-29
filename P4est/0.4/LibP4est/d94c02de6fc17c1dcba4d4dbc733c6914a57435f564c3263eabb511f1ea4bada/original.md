```
sc_recycle_array_insert(rec_array, position)
```

Insert an object into the recycle array. The object is not copied into the array. Use the return value for that.

### Parameters

  * `position`:[out] If position != NULL, *position is set to the array position of the inserted object.

### Returns

Returns the new address of the object in the array.

### Prototype

```c
void *sc_recycle_array_insert (sc_recycle_array_t * rec_array, size_t *position);
```
