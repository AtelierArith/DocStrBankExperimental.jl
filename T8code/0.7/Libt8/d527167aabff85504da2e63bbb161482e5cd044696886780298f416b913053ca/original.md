```
t8_shmem_array_start_writing(array)
```

Enable writing mode for a shmem array. Only some processes may be allowed to write into the array, which is indicated by the return value being non-zero.

!!! note
    This function is MPI collective.


# Arguments

  * `array`:[in,out] Initialized array. Writing will be enabled on certain processes.

# Returns

True if the calling process can write into the array.

### Prototype

```c
int t8_shmem_array_start_writing (t8_shmem_array_t array);
```
