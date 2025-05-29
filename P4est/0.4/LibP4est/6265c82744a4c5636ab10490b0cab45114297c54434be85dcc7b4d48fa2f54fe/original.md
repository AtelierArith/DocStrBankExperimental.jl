```
sc_uint128_chk_bit(input, exponent)
```

Returns the bit_number-th bit of *input*. This function checks a bit of an existing, initialized value.

### Parameters

  * `input`:[in] A pointer to a [`sc_uint128_t`](@ref).
  * `bit_number`:[in] The bit (counted from the right hand side) that is checked by logical and. Require 0 <= *bit_number* < 128.

### Returns

True if the checked bit is set, false if not.

### Prototype

```c
int sc_uint128_chk_bit (const sc_uint128_t * input, int exponent);
```
