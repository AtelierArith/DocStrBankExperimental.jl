```
sc_list_memory_used(list, is_dynamic)
```

Calculate the total memory used by a list.

### Parameters

  * `list`:[in] The list.
  * `is_dynamic`:[in] True if created with [`sc_list_new`](@ref), false if initialized with [`sc_list_init`](@ref)

### Returns

Memory used in bytes.

### Prototype

```c
size_t sc_list_memory_used (sc_list_t * list, int is_dynamic);
```
