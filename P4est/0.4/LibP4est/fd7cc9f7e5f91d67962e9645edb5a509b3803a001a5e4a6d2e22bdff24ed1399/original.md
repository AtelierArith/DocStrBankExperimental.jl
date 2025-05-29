```
sc_uint128_compare(a, b)
```

Compare the [`sc_uint128_t`](@ref) *a* and the [`sc_uint128_t`](@ref) *b*.

### Parameters

  * `a`:[in] A pointer to a [`sc_uint128_t`](@ref).
  * `b`:[in] A pointer to a [`sc_uint128_t`](@ref).

### Returns

Returns -1 if a < b, 1 if a > b and 0 if a == b.

### Prototype

```c
int sc_uint128_compare (const void *a, const void *b);
```
