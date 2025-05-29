```
p8est_lid_bitwise_or(a, b, result)
```

Calculates the bitwise or of the uint128_t *a* and *b*. *a* == *result* is allowed. Furthermore, *a* == *result* and/or *b* == *result* is allowed.

### Parameters

  * `a`:[in] A pointer to a [`p8est_lid_t`](@ref).
  * `b`:[in] A pointer to a [`p8est_lid_t`](@ref).
  * `result`:[out] A pointer to a [`p8est_lid_t`](@ref). The bitwise or of *a* and *b* will be saved in *result*.

### Prototype

```c
void p8est_lid_bitwise_or (const p8est_lid_t * a, const p8est_lid_t * b, p8est_lid_t * result);
```
