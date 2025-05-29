```
sc_uint128_sub_inplace(a, b)
```

Subtracts the uint128_t *b* from the uint128_t *a*. The result is saved in *a*. *a* == *b* is allowed. This function assumes that the result is >= 0.

### Parameters

  * `a`:[in,out] A pointer to a [`sc_uint128_t`](@ref). *a* will be overwritten by *a* - *b*.
  * `b`:[in] A pointer to a [`sc_uint128_t`](@ref).

### Prototype

```c
void sc_uint128_sub_inplace (sc_uint128_t * a, const sc_uint128_t * b);
```
