```
sc_uint128_bitwise_and(a, b, result)
```

Calculates the bitwise and of the uint128_t *a* and the uint128_t *b*. *a* == *result* is allowed. Furthermore, *a* == *result* and/or *b* == *result* is allowed.

### Parameters

  * `a`:[in] A pointer to a [`sc_uint128_t`](@ref).
  * `b`:[in] A pointer to a [`sc_uint128_t`](@ref).
  * `result`:[out] A pointer to a [`sc_uint128_t`](@ref). The bitwise and of *a* and *b* will be saved. in *result*.

### Prototype

```c
void sc_uint128_bitwise_and (const sc_uint128_t * a, const sc_uint128_t * b, sc_uint128_t * result);
```
