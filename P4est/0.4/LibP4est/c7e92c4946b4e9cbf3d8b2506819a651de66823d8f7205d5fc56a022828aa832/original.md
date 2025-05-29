```
sc_array_sort(array, compar)
```

Sorts the array in ascending order wrt. the comparison function.

### Parameters

  * `array`:[in] The array to sort.
  * `compar`:[in] The comparison function to be used.

### Prototype

```c
void sc_array_sort (sc_array_t * array, int (*compar) (const void *, const void *));
```
