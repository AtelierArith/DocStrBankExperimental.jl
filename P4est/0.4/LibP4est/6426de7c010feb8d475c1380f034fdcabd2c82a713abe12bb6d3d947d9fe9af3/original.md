```
sc_uint128_bitwise_or_inplace(a, b)
```

Calculates the bitwise or of the uint128_t *a* and the uint128_t *b*. *a* == *b* is allowed.

### Parameters

  * `a`:[in,out] A pointer to a [`sc_uint128_t`](@ref). The bitwise or will be saved in *a*.
  * `b`:[in] A pointer to a [`sc_uint128_t`](@ref).

### Prototype

```c
void sc_uint128_bitwise_or_inplace (sc_uint128_t * a, const sc_uint128_t * b);
```
