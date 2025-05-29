```
sc_mempool
```

The [`sc_mempool`](@ref) object provides a large pool of equal-size elements. The pool grows dynamically for element allocation. Elements are referenced by their address which never changes. Elements can be freed (that is, returned to the pool) and are transparently reused. If the zero_and_persist option is selected, new elements are initialized to all zeros on creation, and the contents of an element are not touched between freeing and re-returning it.

| Field            | Note                            |
|:---------------- |:------------------------------- |
| elem_size        | size of a single element        |
| elem_count       | number of valid elements        |
| zero_and_persist | Boolean; is set in constructor. |
| mstamp           | fixed-size chunk allocator      |
| freed            | buffers the freed elements      |
