```
sc_hash_array_new(elem_size, hash_fn, equal_fn, user_data)
```

Create a new hash array.

### Parameters

  * `elem_size`:[in] Size of one array element in bytes.
  * `hash_fn`:[in] Function to compute the hash value.
  * `equal_fn`:[in] Function to test two objects for equality.

### Prototype

```c
sc_hash_array_t *sc_hash_array_new (size_t elem_size, sc_hash_function_t hash_fn, sc_equal_function_t equal_fn, void *user_data);
```
