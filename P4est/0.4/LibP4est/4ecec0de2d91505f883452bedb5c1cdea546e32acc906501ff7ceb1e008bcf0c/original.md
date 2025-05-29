```
sc_hash_truncate(hash)
```

Remove all entries from a hash table in O(N).

If the allocator is owned, it calls [`sc_hash_unlink`](@ref) and [`sc_mempool_truncate`](@ref). Otherwise, it calls [`sc_list_reset`](@ref) on every hash slot which is slower.

### Prototype

```c
void sc_hash_truncate (sc_hash_t * hash);
```
