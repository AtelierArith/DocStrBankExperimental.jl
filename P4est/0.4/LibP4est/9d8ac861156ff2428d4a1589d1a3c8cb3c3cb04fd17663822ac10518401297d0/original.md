```
p4est_lid_bitwise_and(a, b, result)
```

Calculates the bitwise and of the uint128_t *a* and the uint128_t *b*. *a* == *result* is allowed. Furthermore, *a* == *result* and/or *b* == *result* is allowed.

### Parameters

  * `a`:[in] A pointer to a [`p4est_lid_t`](@ref).
  * `b`:[in] A pointer to a [`p4est_lid_t`](@ref).
  * `result`:[out] A pointer to a [`p4est_lid_t`](@ref). The bitwise and of *a* and *b* will be saved. in *result*.

### Prototype

```c
void p4est_lid_bitwise_and (const p4est_lid_t * a, const p4est_lid_t * b, p4est_lid_t * result);
```
