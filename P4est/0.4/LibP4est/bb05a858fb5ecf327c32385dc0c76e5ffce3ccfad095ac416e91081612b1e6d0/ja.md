```
p8est_lid_set_bit(input, bit_number)
```

*input*の指数-thビットを1に設定します。この関数は、既存の初期化された値を変更します。

### パラメータ

  * `input`:[in,out] [`p8est_lid_t`](@ref)へのポインタ。
  * `bit_number`:[in] 論理和によって1に設定されるビット（右側から数えたもの）。0 <= *bit_number* < 128が必要です。

### プロトタイプ

```c
void p8est_lid_set_bit (p8est_lid_t * input, int bit_number);
```
