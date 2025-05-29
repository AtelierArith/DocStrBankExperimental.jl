```
t8_shmem_array_end_writing(array)
```

Disable writing mode for a shmem array.

!!! note
    This function is MPI collective.


# Arguments

  * `array`:[in,out] Initialized with writing mode enabled.

# See also

[`t8_shmem_array_start_writing`](@ref).

### Prototype

```c
void t8_shmem_array_end_writing (t8_shmem_array_t array);
```
