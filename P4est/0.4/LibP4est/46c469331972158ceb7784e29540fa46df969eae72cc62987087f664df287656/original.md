```
p8est_lid_bitwise_neg(a, result)
```

Calculates the bitwise negation of the uint128_t *a*. *a* == *result* is allowed.

### Parameters

  * `a`:[in] A pointer to a [`p8est_lid_t`](@ref).
  * `result`:[out] A pointer to a [`p8est_lid_t`](@ref). The bitwise negation of *a* will be saved in *result*.

### Prototype

```c
void p8est_lid_bitwise_neg (const p8est_lid_t * a, p8est_lid_t * result);
```
