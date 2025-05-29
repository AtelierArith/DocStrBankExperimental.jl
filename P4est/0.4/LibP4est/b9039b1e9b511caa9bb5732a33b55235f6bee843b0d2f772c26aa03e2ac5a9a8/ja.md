```
p8est_lid_bitwise_or(a, b, result)
```

uint128_t *a* と *b* のビット単位の論理和を計算します。*a* == *result* は許可されています。さらに、*a* == *result* および/または *b* == *result* も許可されています。

### パラメータ

  * `a`:[in] [`p8est_lid_t`](@ref) へのポインタ。
  * `b`:[in] [`p8est_lid_t`](@ref) へのポインタ。
  * `result`:[out] [`p8est_lid_t`](@ref) へのポインタ。*a* と *b* のビット単位の論理和が *result* に保存されます。

### プロトタイプ

```c
void p8est_lid_bitwise_or (const p8est_lid_t * a, const p8est_lid_t * b, p8est_lid_t * result);
```
