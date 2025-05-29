```
t8_shmem_array_get_array(array)
```

Return a pointer to the data array of a [`t8_shmem_array`](@ref).

!!! note
    Writing mode must be disabled for *array*.


# Arguments

  * `array`:[in] The [`t8_shmem_array`](@ref).

# Returns

A pointer to the data array of *array*.

### Prototype

```c
const void * t8_shmem_array_get_array (t8_shmem_array_t array);
```
