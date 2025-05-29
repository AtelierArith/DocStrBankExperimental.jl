```
p8est_lid_sub(a, b, result)
```

Substracts the [`p8est_lid_t`](@ref) *b* from the [`p8est_lid_t`](@ref) *a*. This function assumes that the result is >= 0. *result* == *a* or *result* == *b* is not allowed. *a* == *b* is allowed.

### Parameters

  * `a`:[in] A pointer to a [`p8est_lid_t`](@ref).
  * `b`:[in] A pointer to a [`p8est_lid_t`](@ref).
  * `result`:[out] A pointer to a [`p8est_lid_t`](@ref). The difference *a* - *b* will be saved in *result*.

### Prototype

```c
void p8est_lid_sub (const p8est_lid_t * a, const p8est_lid_t * b, p8est_lid_t * result);
```
