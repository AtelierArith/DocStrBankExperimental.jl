```
sc_uint128_set_bit(a, exponent)
```

Sets the exponent-th bit of *a* to one and keep all other bits. This function modifies an existing, initialized value.

### Parameters

  * `a`:[in,out] A pointer to a [`sc_uint128_t`](@ref).
  * `exponent`:[in] The bit (0-based from the rightmost bit) that is set to one by logical or. 0 <= *exponent* < 128.

### Prototype

```c
void sc_uint128_set_bit (sc_uint128_t * a, int exponent);
```
