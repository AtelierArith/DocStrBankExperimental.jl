```
p8est_lid_is_equal(a, b)
```

Checks if the [`p8est_lid_t`](@ref) *a* and the [`p8est_lid_t`](@ref) *b* are equal.

### Parameters

  * `a`:[in] A pointer to a [`p8est_lid_t`](@ref).
  * `b`:[in] A pointer to a [`p8est_lid_t`](@ref).

### Returns

Returns a true value if *a* and *b* are equal, false otherwise

### Prototype

```c
int p8est_lid_is_equal (const p8est_lid_t * a, const p8est_lid_t * b);
```
