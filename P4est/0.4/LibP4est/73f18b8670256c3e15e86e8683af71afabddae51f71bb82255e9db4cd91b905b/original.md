```
sc_array_memory_used(array, is_dynamic)
```

Calculate the memory used by an array.

### Parameters

  * `array`:[in] The array.
  * `is_dynamic`:[in] True if created with [`sc_array_new`](@ref), false if initialized with [`sc_array_init`](@ref)

### Returns

Memory used in bytes.

### Prototype

```c
size_t sc_array_memory_used (sc_array_t * array, int is_dynamic);
```
