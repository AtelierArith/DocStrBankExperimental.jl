```
p4est_lid_bitwise_or_inplace(a, b)
```

Calculates the bitwise or of the uint128_t *a* and the uint128_t *b*. *a* == *b* is allowed.

### Parameters

  * `a`:[in,out] A pointer to a [`p4est_lid_t`](@ref). The bitwise or will be saved in *a*.
  * `b`:[in] A pointer to a [`p4est_lid_t`](@ref).

### Prototype

```c
void p4est_lid_bitwise_or_inplace (p4est_lid_t * a, const p4est_lid_t * b);
```
