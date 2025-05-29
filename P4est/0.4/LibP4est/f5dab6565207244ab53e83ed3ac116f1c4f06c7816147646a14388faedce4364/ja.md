```
p8est_lid_copy(input, output)
```

初期化された [`p8est_lid_t`](@ref) を [`p8est_lid_t`](@ref) にコピーします。

### パラメータ

  * `input`:[in] コピーされる [`sc_uint128`](@ref) へのポインタ。
  * `output`:[in,out] [`p8est_lid_t`](@ref) へのポインタ。*output* の高位ビットと低位ビットは、それぞれ *input* の高位ビットと低位ビットに設定されます。

### プロトタイプ

```c
void p8est_lid_copy (const p8est_lid_t * input, p8est_lid_t * output);
```
