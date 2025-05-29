```
sc_array_is_permutation(array)
```

Determine whether *array* is an array of size_t's whose entries include every integer 0 <= i < array->elem_count.

### Parameters

  * `array`:[in] An array.

### Returns

Returns 1 if array contains size_t elements whose entries include every integer 0 <= i < *array*->elem_count, 0 otherwise.

### Prototype

```c
int sc_array_is_permutation (sc_array_t * array);
```
