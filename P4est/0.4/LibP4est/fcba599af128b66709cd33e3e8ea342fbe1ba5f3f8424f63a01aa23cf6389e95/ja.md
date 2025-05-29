```
p8est_lid_bitwise_and_inplace(a, b)
```

uint128*t *a* と uint128*t *b* のビット単位の AND を計算します。 *a* == *b* は許可されています。

### パラメータ

  * `a`:[in,out] [`p8est_lid_t`](@ref) へのポインタ。ビット単位の AND の結果が *a* に保存されます。
  * `b`:[in] [`p8est_lid_t`](@ref) へのポインタ。

### プロトタイプ

```c
void p8est_lid_bitwise_and_inplace (p8est_lid_t * a, const p8est_lid_t * b);
```
