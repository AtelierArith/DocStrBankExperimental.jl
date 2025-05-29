```
t8_shmem_array_destroy(parray)
```

Free all memory associated with a [`t8_shmem_array`](@ref).

# Arguments

  * `parray`:[in,out] On input a pointer to a valid [`t8_shmem_array`](@ref). This array is freed and *parray* is set to NULL on return.

### Prototype

```c
void t8_shmem_array_destroy (t8_shmem_array_t *parray);
```
