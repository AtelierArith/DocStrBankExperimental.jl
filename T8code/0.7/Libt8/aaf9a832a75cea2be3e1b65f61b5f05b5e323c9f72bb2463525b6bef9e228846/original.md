```
t8_shmem_array_index(array, index)
```

Return a read-only pointer to an element in a [`t8_shmem_array`](@ref).

!!! note
    You should not modify the value.


!!! note
    Writing mode must be disabled for *array*.


# Arguments

  * `array`:[in] The [`t8_shmem_array`](@ref).
  * `index`:[in] The index of an element.

# Returns

A pointer to the element at *index* in *array*.

### Prototype

```c
const void * t8_shmem_array_index (t8_shmem_array_t array, size_t index);
```
