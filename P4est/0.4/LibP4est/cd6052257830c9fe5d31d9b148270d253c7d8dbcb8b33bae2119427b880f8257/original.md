```
p4est_lid_copy(input, output)
```

Copies an initialized [`p4est_lid_t`](@ref) to a [`p4est_lid_t`](@ref).

### Parameters

  * `input`:[in] A pointer to the [`p4est_lid_t`](@ref) that is copied.
  * `output`:[in,out] A pointer to a [`p4est_lid_t`](@ref). The low bits of *output* will be set to the low bits of *input* and high bits are ignored.

### Prototype

```c
void p4est_lid_copy (const p4est_lid_t * input, p4est_lid_t * output);
```
