```
t8_shmem_array_copy(dest, source)
```

Copy the contents of one t8_shmem array into another.

!!! note
    *dest* must be initialized and match in element size and element count to *source*.


!!! note
    *dest* must have writing mode disabled.


# Arguments

  * `dest`:[in,out] The array in which *source* should be copied.
  * `source`:[in] The array to copy.

### Prototype

```c
void t8_shmem_array_copy (t8_shmem_array_t dest, t8_shmem_array_t source);
```
