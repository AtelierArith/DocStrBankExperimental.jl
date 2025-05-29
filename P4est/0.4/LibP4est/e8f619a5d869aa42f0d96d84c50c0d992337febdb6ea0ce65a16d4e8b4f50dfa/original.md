```
sc_uint128_bitwise_neg(a, result)
```

Calculates the bitwise negation of the uint128_t *a*. *a* == *result* is allowed.

### Parameters

  * `a`:[in] A pointer to a [`sc_uint128_t`](@ref).
  * `result`:[out] A pointer to a [`sc_uint128_t`](@ref). The bitwise negation of *a* will be saved in *result*.

### Prototype

```c
void sc_uint128_bitwise_neg (const sc_uint128_t * a, sc_uint128_t * result);
```
