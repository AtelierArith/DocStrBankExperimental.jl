```
sc_array_pqueue_add(array, temp, compar)
```

Adds an element to a priority queue. PQUEUE FUNCTIONS ARE UNTESTED AND CURRENTLY DISABLED. This function is not allowed for views. The priority queue is implemented as a heap in ascending order. A heap is a binary tree where the children are not less than their parent. Assumes that elements [0]..[elem_count-2] form a valid heap. Then propagates [elem_count-1] upward by swapping if necessary.

!!! note
    If the return value is zero for all elements in an array, the array is sorted linearly and unchanged.


### Parameters

  * `temp`:[in] Pointer to unused allocated memory of elem_size.
  * `compar`:[in] The comparison function to be used.

### Returns

Returns the number of swap operations.

### Prototype

```c
size_t sc_array_pqueue_add (sc_array_t * array, void *temp, int (*compar) (const void *, const void *));
```
