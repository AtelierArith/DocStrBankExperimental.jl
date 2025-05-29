```
sc_uint128_set_bit(a, exponent)
```

  * *a* の exponent 番目のビットを 1 に設定し、他のすべてのビットを保持します。この関数は、既存の初期化された値を変更します。

### パラメータ

  * `a`:[in,out] [`sc_uint128_t`](@ref) へのポインタ。
  * `exponent`:[in] 論理和によって 1 に設定されるビット (最右ビットから 0 ベース)。0 <= *exponent* < 128。

### プロトタイプ

```c
void sc_uint128_set_bit (sc_uint128_t * a, int exponent);
```
