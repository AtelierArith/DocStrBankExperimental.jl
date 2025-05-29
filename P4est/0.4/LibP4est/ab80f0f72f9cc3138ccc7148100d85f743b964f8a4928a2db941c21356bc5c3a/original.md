```
p4est_lid_shift_right(input, shift_count, result)
```

Calculates the bit right shift of uint128_t *input* by shift_count bits. We shift in zeros from the left. If *shift_count* >= 64, *result* is 0. All bits right from the zeroth bit (counted from the right hand side) drop out. *input* == *result* is allowed.

### Parameters

  * `input`:[in] A pointer to a [`p4est_lid_t`](@ref).
  * `shift_count`:[in] Bits to shift. *shift_count* >= 0.
  * `result`:[in,out] A pointer to a [`p4est_lid_t`](@ref). The right shifted number will be saved in *result*.

### Prototype

```c
void p4est_lid_shift_right (const p4est_lid_t * input, unsigned shift_count, p4est_lid_t * result);
```
