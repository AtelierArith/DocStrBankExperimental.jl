```
p4est_lid_sub_inplace(a, b)
```

uint128*t *b*をuint128*t *a*から引き算します。結果は*a*に保存されます。*a* == *b*は許可されています。この関数は、結果が>= 0であることを前提としています。

### パラメータ

  * `a`:[in,out] [`p4est_lid_t`](@ref)へのポインタ。*a*は*a* - *b*で上書きされます。
  * `b`:[in] [`p4est_lid_t`](@ref)へのポインタ。

### プロトタイプ

```c
void p4est_lid_sub_inplace (p4est_lid_t * a, const p4est_lid_t * b);
```
