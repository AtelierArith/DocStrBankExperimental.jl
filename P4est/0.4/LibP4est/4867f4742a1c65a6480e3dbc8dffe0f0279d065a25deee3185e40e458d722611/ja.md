```
p4est_lid_set_bit(input, bit_number)
```

  * a の exponent-th ビットを 1 に設定します。この関数は、既存の初期化された値を変更します。

### パラメータ

  * `input`:[in,out] [`p4est_lid_t`](@ref) へのポインタ。
  * `bit_number`:[in] 論理和によって 1 に設定されるビット（右側から数えたもの）。0 <= *bit_number* < 64 が必要です。

### プロトタイプ

```c
void p4est_lid_set_bit (p4est_lid_t * input, int bit_number);
```
