```
t8_shmem_array_get_gloidx_array_for_writing(array)
```

Return a pointer to the data of a shared memory array interpreted as an [`t8_gloidx_t`](@ref) array. The array must have writing enabled t8*shmem*array*start*writing and you should not write into the memory after t8*shmem*array*end*writing was called.

# Arguments

  * `array`:[in] The [`t8_shmem_array`](@ref)

# Returns

The data of *array* as [`t8_gloidx_t`](@ref) pointer.

### Prototype

```c
t8_gloidx_t * t8_shmem_array_get_gloidx_array_for_writing (t8_shmem_array_t array);
```
