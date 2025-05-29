```
sc_uint128_sub(a, b, result)
```

Subtracts the uint128_t *b* from the uint128_t *a*. This function assumes that the result is >= 0. *result* == *a* or *result* == *b* is not allowed. *a* == *b* is allowed.

### Parameters

  * `a`:[in] A pointer to a [`sc_uint128_t`](@ref).
  * `b`:[in] A pointer to a [`sc_uint128_t`](@ref).
  * `result`:[out] A pointer to a [`sc_uint128_t`](@ref). The difference *a* - *b* will be saved in *result*.

### Prototype

```c
void sc_uint128_sub (const sc_uint128_t * a, const sc_uint128_t * b, sc_uint128_t * result);
```
