```
sc_hash_function_string(s, u)
```

Compute a hash value from a null-terminated string. This hash function is NOT cryptographically safe! Use libcrypt then.

### Parameters

  * `s`:[in] Null-terminated string to be hashed.
  * `u`:[in] Not used.

### Returns

The computed hash value as an unsigned integer.

### Prototype

```c
unsigned int sc_hash_function_string (const void *s, const void *u);
```
