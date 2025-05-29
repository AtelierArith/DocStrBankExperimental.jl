```
p4est_lid_init(input, high, low)
```

Initializes an unsigned 64 bit integer. *high* is just a a placeholder to use the same interface in 3D.

### Parameters

  * `input`:[in,out] A pointer to a [`p4est_lid_t`](@ref) that will be intialized.
  * `high`:[in] The given high bits must be zero.
  * `low`:[in] The given low bits to initialize *input*.

### Prototype

```c
void p4est_lid_init (p4est_lid_t * input, uint64_t high, uint64_t low);
```
