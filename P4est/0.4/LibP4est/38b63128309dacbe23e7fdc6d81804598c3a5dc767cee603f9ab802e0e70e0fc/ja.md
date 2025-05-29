```
sc_uint128_copy(input, output)
```

初期化された [`sc_uint128_t`](@ref) を [`sc_uint128_t`](@ref) にコピーします。

### パラメータ

  * `input`:[in] コピーされる [`sc_uint128`](@ref) へのポインタ。
  * `output`:[in,out] [`sc_uint128_t`](@ref) へのポインタ。*output* の高位ビットと低位ビットは、それぞれ *input* の高位ビットと低位ビットに設定されます。

### プロトタイプ

```c
void sc_uint128_copy (const sc_uint128_t * input, sc_uint128_t * output);
```
