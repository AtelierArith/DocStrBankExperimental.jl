```
sc_uint128_add(a, b, result)
```

Adds the uint128_t *b* to the uint128_t *a*. *result* == *a* or *result* == *b* is not allowed. *a* == *b* is allowed.

### Parameters

  * `a`:[in] A pointer to a [`sc_uint128_t`](@ref).
  * `b`:[in] A pointer to a [`sc_uint128_t`](@ref).
  * `result`:[out] A pointer to a [`sc_uint128_t`](@ref). The sum *a* + *b* will be saved in *result*.

### Prototype

```c
void sc_uint128_add (const sc_uint128_t * a, const sc_uint128_t * b, sc_uint128_t * result);
```
