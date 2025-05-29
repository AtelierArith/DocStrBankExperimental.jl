```
p8est_lid_copy(input, output)
```

Copies an initialized [`p8est_lid_t`](@ref) to a [`p8est_lid_t`](@ref).

### Parameters

  * `input`:[in] A pointer to the [`sc_uint128`](@ref) that is copied.
  * `output`:[in,out] A pointer to a [`p8est_lid_t`](@ref). The high and low bits of *output* will be set to the high and low bits of *input*, respectively.

### Prototype

```c
void p8est_lid_copy (const p8est_lid_t * input, p8est_lid_t * output);
```
