```
sc_uint128_copy(input, output)
```

Copies an initialized [`sc_uint128_t`](@ref) to a [`sc_uint128_t`](@ref).

### Parameters

  * `input`:[in] A pointer to the [`sc_uint128`](@ref) that is copied.
  * `output`:[in,out] A pointer to a [`sc_uint128_t`](@ref). The high and low bits of *output* will be set to the high and low bits of *input*, respectively.

### Prototype

```c
void sc_uint128_copy (const sc_uint128_t * input, sc_uint128_t * output);
```
