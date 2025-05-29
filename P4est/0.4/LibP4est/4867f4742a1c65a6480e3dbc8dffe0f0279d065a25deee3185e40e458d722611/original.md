```
p4est_lid_set_bit(input, bit_number)
```

Sets the exponent-th bit of *a* to one. This function modifies an existing, initialized value.

### Parameters

  * `input`:[in,out] A pointer to a [`p4est_lid_t`](@ref).
  * `bit_number`:[in] The bit (counted from the right hand side) that is set to one by logical or. Require 0 <= *bit_number* < 64.

### Prototype

```c
void p4est_lid_set_bit (p4est_lid_t * input, int bit_number);
```
