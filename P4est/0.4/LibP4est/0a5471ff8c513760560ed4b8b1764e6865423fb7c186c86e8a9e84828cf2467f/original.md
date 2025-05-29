```
sc_hash_array_rip(hash_array, rip)
```

Extract the array data from a hash array and destroy everything else.

### Parameters

  * `hash_array`:[in] The hash array is destroyed after extraction.
  * `rip`:[in] Array structure that will be overwritten. All previous array data (if any) will be leaked. The filled array can be freed with [`sc_array_reset`](@ref).

### Prototype

```c
void sc_hash_array_rip (sc_hash_array_t * hash_array, sc_array_t * rip);
```
