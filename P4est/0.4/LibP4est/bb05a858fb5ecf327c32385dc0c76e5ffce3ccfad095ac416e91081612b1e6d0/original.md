```
p8est_lid_set_bit(input, bit_number)
```

Sets the exponent-th bit of *input* to one. This function modifies an existing, initialized value.

### Parameters

  * `input`:[in,out] A pointer to a [`p8est_lid_t`](@ref).
  * `bit_number`:[in] The bit (counted from the right hand side) that is set to one by logical or. Require 0 <= *bit_number* < 128.

### Prototype

```c
void p8est_lid_set_bit (p8est_lid_t * input, int bit_number);
```
