```
sc_hash_destroy(hash)
```

Destroy a hash table.

If the allocator is owned, this runs in O(1), otherwise in O(N).

!!! note
    If allocator was provided in [`sc_hash_new`](@ref), it will not be destroyed.


### Prototype

```c
void sc_hash_destroy (sc_hash_t * hash);
```
