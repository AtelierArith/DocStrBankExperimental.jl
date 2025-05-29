```
p8est_lid_chk_bit(input, bit_number)
```

*input*のbit_number番目のビットを返します。この関数は、既存の初期化された値のビットをチェックします。

### パラメータ

  * `input`:[in] [`p8est_lid_t`](@ref)へのポインタ。
  * `bit_number`:[in] 論理積でチェックされるビット（右側から数えた場合）。0 <= *bit_number* < 128が必要です。

### 戻り値

ビットがセットされていれば真、そうでなければ偽。

### プロトタイプ

```c
int p8est_lid_chk_bit (const p8est_lid_t * input, int bit_number);
```
