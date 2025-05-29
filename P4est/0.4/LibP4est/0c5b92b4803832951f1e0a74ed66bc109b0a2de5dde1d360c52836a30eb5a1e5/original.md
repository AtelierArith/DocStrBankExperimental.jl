```
sc_array_bsearch(array, key, compar)
```

Performs a binary search on an array. The array must be sorted.

### Parameters

  * `array`:[in] A sorted array to search in.
  * `key`:[in] An element to be searched for.
  * `compar`:[in] The comparison function to be used.

### Returns

Returns the index into array for the item found, or -1.

### Prototype

```c
ssize_t sc_array_bsearch (sc_array_t * array, const void *key, int (*compar) (const void *, const void *));
```
