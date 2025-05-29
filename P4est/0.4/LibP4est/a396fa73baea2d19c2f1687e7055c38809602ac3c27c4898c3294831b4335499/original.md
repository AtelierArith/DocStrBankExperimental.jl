```
sc_uint128_add_inplace(a, b)
```

Adds the uint128 *b* to the uint128_t *a*. The result is saved in *a*. *a* == *b* is allowed.

### Parameters

  * `a`:[in,out] A pointer to a [`sc_uint128_t`](@ref). *a* will be overwritten by *a* + *b*.
  * `b`:[in] A pointer to a [`sc_uint128_t`](@ref).

### Prototype

```c
void sc_uint128_add_inplace (sc_uint128_t * a, const sc_uint128_t * b);
```
