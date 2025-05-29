```
p8est_lid_sub(a, b, result)
```

[`p8est_lid_t`](@ref) *b* を [`p8est_lid_t`](@ref) *a* から引き算します。この関数は、結果が >= 0 であることを前提としています。 *result* == *a* または *result* == *b* は許可されていません。 *a* == *b* は許可されています。

### パラメータ

  * `a`:[in] [`p8est_lid_t`](@ref) へのポインタ。
  * `b`:[in] [`p8est_lid_t`](@ref) へのポインタ。
  * `result`:[out] [`p8est_lid_t`](@ref) へのポインタ。差 *a* - *b* が *result* に保存されます。

### プロトタイプ

```c
void p8est_lid_sub (const p8est_lid_t * a, const p8est_lid_t * b, p8est_lid_t * result);
```
