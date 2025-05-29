```
sc_uint128_shift_right(input, shift_count, result)
```

Calculates the bit right shift of uint128_t *input* by shift_count bits. We shift in zeros from the left. If *shift_count* >= 128, *result* is 0. All bits right from the zeroth bit (counted from the right hand side) drop out. *input* == *result* is allowed.

### Parameters

  * `input`:[in] A pointer to a [`sc_uint128_t`](@ref).
  * `shift_count`:[in] Bits to shift. *shift_count* >= 0.
  * `result`:[in,out] A pointer to a [`sc_uint128_t`](@ref). The right shifted number will be saved in *result*.

### Prototype

```c
void sc_uint128_shift_right (const sc_uint128_t * input, int shift_count, sc_uint128_t * result);
```
