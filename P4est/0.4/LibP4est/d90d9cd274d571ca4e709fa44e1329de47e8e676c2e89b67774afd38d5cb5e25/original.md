```
p4est_lid_is_equal(a, b)
```

Checks if the [`p4est_lid_t`](@ref) *a* and the [`p4est_lid_t`](@ref) *b* are equal.

### Parameters

  * `a`:[in] A pointer to a [`p4est_lid_t`](@ref).
  * `b`:[in] A pointer to a [`p4est_lid_t`](@ref).

### Returns

Returns a true value if *a* and *b* are equal, false otherwise

### Prototype

```c
int p4est_lid_is_equal (const p4est_lid_t * a, const p4est_lid_t * b);
```
