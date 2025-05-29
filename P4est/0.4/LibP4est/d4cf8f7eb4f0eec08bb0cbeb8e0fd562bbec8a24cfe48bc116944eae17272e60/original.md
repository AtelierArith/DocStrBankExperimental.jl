```
p8est_lid_init(input, high, low)
```

Initializes a linear index to a given value.

### Parameters

  * `a`:[in,out] A pointer to the [`p8est_lid_t`](@ref) that will be initialized.
  * `high`:[in] The given high bits to intialize *a*.
  * `low`:[in] The given low bits to initialize *a*.

### Prototype

```c
void p8est_lid_init (p8est_lid_t * input, uint64_t high, uint64_t low);
```
