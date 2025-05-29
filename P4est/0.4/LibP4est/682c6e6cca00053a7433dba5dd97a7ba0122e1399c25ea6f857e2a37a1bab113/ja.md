```
p4est_lid_bitwise_or_inplace(a, b)
```

uint128*t *a* と uint128*t *b* のビット単位の論理和を計算します。 *a* == *b* は許可されています。

### パラメータ

  * `a`:[in,out] [`p4est_lid_t`](@ref) へのポインタ。ビット単位の論理和は *a* に保存されます。
  * `b`:[in] [`p4est_lid_t`](@ref) へのポインタ。

### プロトタイプ

```c
void p4est_lid_bitwise_or_inplace (p4est_lid_t * a, const p4est_lid_t * b);
```
