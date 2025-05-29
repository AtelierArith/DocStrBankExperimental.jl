```
p4est_lid_chk_bit(input, bit_number)
```

Returns the bit_number-th bit of *input*. This function checks a bit of an existing, initialized value.

### Parameters

  * `input`:[in] A pointer to a [`p4est_lid_t`](@ref).
  * `bit_number`:[in] The bit (counted from the right hand side) that is checked by logical and. Require 0 <= *bit_number* < 64.

### Returns

True if bit is set, false if not.

### Prototype

```c
int p4est_lid_chk_bit (const p4est_lid_t * input, int bit_number);
```
