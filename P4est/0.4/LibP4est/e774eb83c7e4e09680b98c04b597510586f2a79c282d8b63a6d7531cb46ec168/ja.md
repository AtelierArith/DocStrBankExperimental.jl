```
p8est_lid_shift_left(input, shift_count, result)
```

uint128*t *input* のビットを shift*count ビット左にシフトします。右からゼロをシフトインします。*shift_count* >= 128 の場合、*result* は 0 になります。127 ビット目（右側からゼロベースでカウント）より左のすべてのビットは落ちます。*input* == *result* は許可されています。

### パラメータ

  * `input`:[in] [`p8est_lid_t`](@ref) へのポインタ。
  * `shift_count`:[in] シフトするビット数。*shift_count* >= 0。
  * `result`:[in,out] [`p8est_lid_t`](@ref) へのポインタ。左にシフトされた数値が *result* に保存されます。

### プロトタイプ

```c
void p8est_lid_shift_left (const p8est_lid_t * input, unsigned shift_count, p8est_lid_t * result);
```
