```
sc_uint128_shift_left(input, shift_count, result)
```

uint128*t *input* のビットを shift*count ビット左にシフトします。右からゼロをシフトインします。*shift_count* >= 128 の場合、*result* は 0 になります。127 ビット目（右側からゼロベースでカウント）より左のすべてのビットは落ちます。*input* == *result* は許可されています。

### パラメータ

  * `input`:[in] [`sc_uint128_t`](@ref) へのポインタ。
  * `shift_count`:[in] シフトするビット数。*shift_count* >= 0。
  * `result`:[in,out] [`sc_uint128_t`](@ref) へのポインタ。左シフトされた数値が *result* に保存されます。

### プロトタイプ

```c
void sc_uint128_shift_left (const sc_uint128_t * input, int shift_count, sc_uint128_t * result);
```
