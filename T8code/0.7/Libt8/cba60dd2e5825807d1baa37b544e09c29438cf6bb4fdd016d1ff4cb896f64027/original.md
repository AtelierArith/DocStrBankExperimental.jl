```
t8_sc_array_index_locidx(array, it)
```

Return a pointer to an array element indexed by a [`t8_locidx_t`](@ref).

# Arguments

  * `index`:[in] needs to be in [0]..[elem_count-1].

# Returns

A void * pointing to entry *it* in *array*.

### Prototype

```c
void * t8_sc_array_index_locidx (const sc_array_t *array, const t8_locidx_t it);
```
