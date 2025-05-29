```
p4est_lid_add(a, b, result)
```

Adds the uint128_t *b* to the uint128_t *a*. *result* == *a* or *result* == *b* is not allowed. *a* == *b* is allowed.

### Parameters

  * `a`:[in] A pointer to a [`p4est_lid_t`](@ref).
  * `b`:[in] A pointer to a [`p4est_lid_t`](@ref).
  * `result`:[out] A pointer to a [`p4est_lid_t`](@ref). The sum *a* + *b* will be saved in *result*.

### Prototype

```c
void p4est_lid_add (const p4est_lid_t * a, const p4est_lid_t * b, p4est_lid_t * result);
```
