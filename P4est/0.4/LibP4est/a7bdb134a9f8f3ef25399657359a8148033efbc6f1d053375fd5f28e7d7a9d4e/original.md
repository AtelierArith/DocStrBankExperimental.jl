```
sc_hash_new(hash_fn, equal_fn, user_data, allocator)
```

Create a new hash table. The number of hash slots is chosen dynamically.

### Parameters

  * `hash_fn`:[in] Function to compute the hash value.
  * `equal_fn`:[in] Function to test two objects for equality.
  * `user_data`:[in] User data passed through to the hash function.
  * `allocator`:[in] Memory allocator for [`sc_link_t`](@ref), can be NULL.

### Prototype

```c
sc_hash_t *sc_hash_new (sc_hash_function_t hash_fn, sc_equal_function_t equal_fn, void *user_data, sc_mempool_t * allocator);
```
