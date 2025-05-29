```
p8est_lid_bitwise_and_inplace(a, b)
```

Calculates the bitwise and of the uint128_t *a* and the uint128_t *b*. *a* == *b* is allowed.

### Parameters

  * `a`:[in,out] A pointer to a [`p8est_lid_t`](@ref). The bitwise and will be saved in *a*.
  * `b`:[in] A pointer to a [`p8est_lid_t`](@ref).

### Prototype

```c
void p8est_lid_bitwise_and_inplace (p8est_lid_t * a, const p8est_lid_t * b);
```
