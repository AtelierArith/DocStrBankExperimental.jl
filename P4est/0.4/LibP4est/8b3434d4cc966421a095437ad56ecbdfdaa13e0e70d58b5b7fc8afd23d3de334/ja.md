```
p4est_lid_sub(a, b, result)
```

[`p4est_lid_t`](@ref) *b* を [`p4est_lid_t`](@ref) *a* から引き算します。この関数は、結果が >= 0 であることを前提としています。 *result* == *a* または *result* == *b* は許可されていません。 *a* == *b* は許可されています。

### パラメータ

  * `a`:[in] [`p4est_lid_t`](@ref) へのポインタ。
  * `b`:[in] [`p4est_lid_t`](@ref) へのポインタ。
  * `result`:[out] [`p4est_lid_t`](@ref) へのポインタ。差分 *a* - *b* が *result* に保存されます。

### プロトタイプ

```c
void p4est_lid_sub (const p4est_lid_t * a, const p4est_lid_t * b, p4est_lid_t * result);
```
