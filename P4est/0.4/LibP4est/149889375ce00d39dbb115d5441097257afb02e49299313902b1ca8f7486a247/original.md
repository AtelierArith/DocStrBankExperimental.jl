```
sc_array_is_sorted(array, compar)
```

Check whether the array is sorted wrt. the comparison function.

### Parameters

  * `array`:[in] The array to check.
  * `compar`:[in] The comparison function to be used.

### Returns

True if array is sorted, false otherwise.

### Prototype

```c
int sc_array_is_sorted (sc_array_t * array, int (*compar) (const void *, const void *));
```
