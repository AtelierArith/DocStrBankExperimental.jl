```
sc_array_uniq(array, compar)
```

Removed duplicate entries from a sorted array. This function is not allowed for views.

### Parameters

  * `array`:[in,out] The array size will be reduced as necessary.
  * `compar`:[in] The comparison function to be used.

### Prototype

```c
void sc_array_uniq (sc_array_t * array, int (*compar) (const void *, const void *));
```
