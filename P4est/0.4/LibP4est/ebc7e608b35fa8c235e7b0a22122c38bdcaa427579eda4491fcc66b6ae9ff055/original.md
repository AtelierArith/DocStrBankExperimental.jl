```
p8est_lid_add_inplace(a, b)
```

Adds the [`p8est_lid_t`](@ref) *b* to the [`p8est_lid_t`](@ref) *a*. The result is saved in *a*. *a* == *b* is allowed.

### Parameters

  * `a`:[in,out] A pointer to a [`p8est_lid_t`](@ref). *a* will be overwritten by *a* + *b*.
  * `b`:[in] A pointer to a [`p8est_lid_t`](@ref).

### Prototype

```c
void p8est_lid_add_inplace (p8est_lid_t * a, const p8est_lid_t * b);
```
