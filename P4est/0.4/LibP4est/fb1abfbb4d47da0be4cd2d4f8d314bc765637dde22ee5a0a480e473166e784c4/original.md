```
sc_list_new(allocator)
```

Allocate a new, empty linked list.

### Parameters

  * `allocator`:[in] Memory allocator for [`sc_link_t`](@ref), can be NULL in which case an internal allocator is created.

### Returns

Pointer to a newly allocated, empty list object.

### Prototype

```c
sc_list_t *sc_list_new (sc_mempool_t * allocator);
```
