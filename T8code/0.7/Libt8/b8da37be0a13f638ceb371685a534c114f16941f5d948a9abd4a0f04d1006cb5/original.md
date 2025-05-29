```
t8_shmem_array_set_gloidx(array, index, value)
```

Set an entry of a t8_shmem array that is used to store [`t8_gloidx_t`](@ref). The array must have writing mode enabled t8*shmem*array*start*writing.

# Arguments

  * `array`:[in,out] The array to be modified.
  * `index`:[in] The array entry to be modified.
  * `value`:[in] The new value to be set.

### Prototype

```c
void t8_shmem_array_set_gloidx (t8_shmem_array_t array, int index, t8_gloidx_t value);
```
