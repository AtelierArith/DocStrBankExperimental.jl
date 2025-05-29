```
p4est_lid_shift_left(input, shift_count, result)
```

uint128*t *input* のビットを shift*count ビット左にシフトします。右からゼロをシフトインします。*shift_count* >= 64 の場合、*result* は 0 になります。63 番目のビット（右側からゼロベースでカウント）より左のすべてのビットは落ちます。*input* == *result* は許可されています。

### パラメータ

  * `input`:[in] [`p4est_lid_t`](@ref) へのポインタ。
  * `shift_count`:[in] シフトするビット数。*shift_count* >= 0。
  * `result`:[in,out] [`p4est_lid_t`](@ref) へのポインタ。左にシフトされた数値が *result* に保存されます。

### プロトタイプ

```c
void p4est_lid_shift_left (const p4est_lid_t * input, unsigned shift_count, p4est_lid_t * result);
```
