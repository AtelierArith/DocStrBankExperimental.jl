```
sc_uint128_shift_left(input, shift_count, result)
```

Calculates the bit left shift of uint128_t *input* by shift_count bits. We shift in zeros from the right. If *shift_count* >= 128, *result* is 0. All bits left from the 127th bit (counted zero based from the right hand side) drop out. *input* == *result* is allowed.

### Parameters

  * `input`:[in] A pointer to a [`sc_uint128_t`](@ref).
  * `shift_count`:[in] Bits to shift. *shift_count* >= 0.
  * `result`:[in,out] A pointer to a [`sc_uint128_t`](@ref). The left shifted number will be saved in *result*.

### Prototype

```c
void sc_uint128_shift_left (const sc_uint128_t * input, int shift_count, sc_uint128_t * result);
```
