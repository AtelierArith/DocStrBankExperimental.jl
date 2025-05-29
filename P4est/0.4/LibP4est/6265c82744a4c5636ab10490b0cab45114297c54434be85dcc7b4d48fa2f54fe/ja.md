```
sc_uint128_chk_bit(input, exponent)
```

*input*のbit_number番目のビットを返します。この関数は、既存の初期化された値のビットをチェックします。

### パラメータ

  * `input`:[in] [`sc_uint128_t`](@ref)へのポインタ。
  * `bit_number`:[in] 論理積によってチェックされるビット（右側から数えたもの）。0 <= *bit_number* < 128が必要です。

### 戻り値

チェックされたビットがセットされていれば真、そうでなければ偽です。

### プロトタイプ

```c
int sc_uint128_chk_bit (const sc_uint128_t * input, int exponent);
```
