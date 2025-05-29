```
t8_shmem_array_index_for_writing(array, index)
```

Return a pointer to an element in a [`t8_shmem_array`](@ref) in writing mode.

!!! note
    You can modify the value before the next call to t8*shmem*array*end*writing.


!!! note
    Writing mode must be enabled for *array*.


# Arguments

  * `array`:[in] The [`t8_shmem_array`](@ref).
  * `index`:[in] The index of an element.

# Returns

A pointer to the element at *index* in *array*.

### Prototype

```c
void * t8_shmem_array_index_for_writing (t8_shmem_array_t array, size_t index);
```
