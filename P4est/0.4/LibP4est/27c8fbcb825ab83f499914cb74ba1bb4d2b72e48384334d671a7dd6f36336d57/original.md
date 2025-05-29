```
p8est_lid_compare(a, b)
```

Compare the [`p8est_lid_t`](@ref) *a* and the [`p8est_lid_t`](@ref) *b*.

### Parameters

  * `a`:[in] A pointer to a [`p8est_lid_t`](@ref).
  * `b`:[in] A pointer to a [`p8est_lid_t`](@ref).

### Returns

Returns -1 if a < b, 1 if a > b and 0 if a == b.

### Prototype

```c
int p8est_lid_compare (const p8est_lid_t * a, const p8est_lid_t * b);
```
