```
p8est_lid_sub_inplace(a, b)
```

uint128*t *b* を uint128*t *a* から引き算します。結果は *a* に保存されます。*a* == *b* は許可されています。この関数は、結果が >= 0 であることを前提としています。

### パラメータ

  * `a`:[in,out] [`p8est_lid_t`](@ref) へのポインタ。*a* は *a* - *b* によって上書きされます。
  * `b`:[in] [`p8est_lid_t`](@ref) へのポインタ。

### プロトタイプ

```c
void p8est_lid_sub_inplace (p8est_lid_t * a, const p8est_lid_t * b);
```
