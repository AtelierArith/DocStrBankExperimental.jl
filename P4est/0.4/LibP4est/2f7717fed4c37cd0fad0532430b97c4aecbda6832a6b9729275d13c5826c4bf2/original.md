```
sc_array
```

The [`sc_array`](@ref) object provides a dynamic array of equal-size elements. Elements are accessed by their 0-based index. Their address may change. The number of elements (== elem_count) of the array can be changed by  sc*array*resize and sc*array*rewind. Elements can be sorted with sc*array*sort. If the array is sorted, it can be searched with sc*array*bsearch. A priority queue is implemented with pqueue_add and pqueue_pop (untested).

| Field      | Note                                                                                                                                           |
|:---------- |:---------------------------------------------------------------------------------------------------------------------------------------------- |
| elem_size  | size of a single element                                                                                                                       |
| elem_count | number of valid elements                                                                                                                       |
| byte_alloc | number of allocated bytes or -(number of viewed bytes + 1) if this is a view: the "+ 1" distinguishes an array of size 0 from a view of size 0 |
| array      | linear array to store elements                                                                                                                 |
