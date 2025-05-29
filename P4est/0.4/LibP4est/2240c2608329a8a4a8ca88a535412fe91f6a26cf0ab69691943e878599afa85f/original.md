```
sc_hash_unlink(hash)
```

Unlink all hash elements without returning them to the mempool.

If the allocator is not owned, this runs faster than [`sc_hash_truncate`](@ref), but is dangerous because of potential memory leaks.

### Parameters

  * `hash`:[in,out] Hash structure to be unlinked.

### Prototype

```c
void sc_hash_unlink (sc_hash_t * hash);
```
