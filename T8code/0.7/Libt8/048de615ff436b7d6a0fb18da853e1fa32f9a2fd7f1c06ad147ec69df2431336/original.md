```
t8_shmem_array_get_gloidx_array(array)
```

Return a read-only pointer to the data of a shared memory array interpreted as an [`t8_gloidx_t`](@ref) array.

!!! note
    Writing mode must be disabled for *array*.


# Arguments

  * `array`:[in] The [`t8_shmem_array`](@ref)

# Returns

The data of *array* as [`t8_gloidx_t`](@ref) pointer.

### Prototype

```c
const t8_gloidx_t * t8_shmem_array_get_gloidx_array (t8_shmem_array_t array);
```
