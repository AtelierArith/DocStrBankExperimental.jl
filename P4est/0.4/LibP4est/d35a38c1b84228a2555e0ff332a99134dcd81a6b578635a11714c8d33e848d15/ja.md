```
p4est_lid_bitwise_neg(a, result)
```

uint128_t *a*のビット単位の否定を計算します。*a* == *result*は許可されています。

### パラメータ

  * `a`:[in] [`p4est_lid_t`](@ref)へのポインタ。
  * `result`:[out] [`p4est_lid_t`](@ref)へのポインタ。*a*のビット単位の否定が*result*に保存されます。

### プロトタイプ

```c
void p4est_lid_bitwise_neg (const p4est_lid_t * a, p4est_lid_t * result);
```
