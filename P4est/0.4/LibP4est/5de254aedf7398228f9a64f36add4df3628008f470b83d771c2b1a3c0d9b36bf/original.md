```
p8est_lid_sub_inplace(a, b)
```

Substracts the uint128_t *b* from the uint128_t *a*. The result is saved in *a*. *a* == *b* is allowed. This function assumes that the result is >= 0.

### Parameters

  * `a`:[in,out] A pointer to a [`p8est_lid_t`](@ref). *a* will be overwritten by *a* - *b*.
  * `b`:[in] A pointer to a [`p8est_lid_t`](@ref).

### Prototype

```c
void p8est_lid_sub_inplace (p8est_lid_t * a, const p8est_lid_t * b);
```
