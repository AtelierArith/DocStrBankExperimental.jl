```
t8_shmem_array_get_gloidx(array, index)
```

Return an entry of a shared memory array that stores [`t8_gloidx_t`](@ref).

!!! note
    Writing mode must be disabled for *array*.


# Arguments

  * `array`:[in] The [`t8_shmem_array`](@ref)
  * `index`:[in] The index of the entry to be queried.

# Returns

The *index*-th entry of *array* as [`t8_gloidx_t`](@ref).

### Prototype

```c
t8_gloidx_t t8_shmem_array_get_gloidx (t8_shmem_array_t array, int index);
```
