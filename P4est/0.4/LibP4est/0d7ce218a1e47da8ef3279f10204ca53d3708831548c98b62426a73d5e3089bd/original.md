```
sc_array_pqueue_pop(array, result, compar)
```

Pops the smallest element from a priority queue. PQUEUE FUNCTIONS ARE UNTESTED AND CURRENTLY DISABLED. This function is not allowed for views. This function assumes that the array forms a valid heap in ascending order.

!!! note
    This function resizes the array to elem_count-1.


### Parameters

  * `result`:[out] Pointer to unused allocated memory of elem_size.
  * `compar`:[in] The comparison function to be used.

### Returns

Returns the number of swap operations.

### Prototype

```c
size_t sc_array_pqueue_pop (sc_array_t * array, void *result, int (*compar) (const void *, const void *));
```
