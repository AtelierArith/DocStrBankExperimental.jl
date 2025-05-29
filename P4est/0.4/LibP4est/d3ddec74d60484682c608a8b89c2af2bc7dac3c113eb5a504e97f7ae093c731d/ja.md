```
p4est_lid_add(a, b, result)
```

uint128*t *b*をuint128*t *a*に加算します。 *result* == *a* または *result* == *b* は許可されていません。 *a* == *b* は許可されています。

### パラメータ

  * `a`:[in] [`p4est_lid_t`](@ref)へのポインタ。
  * `b`:[in] [`p4est_lid_t`](@ref)へのポインタ。
  * `result`:[out] [`p4est_lid_t`](@ref)へのポインタ。合計 *a* + *b* が *result* に保存されます。

### プロトタイプ

```c
void p4est_lid_add (const p4est_lid_t * a, const p4est_lid_t * b, p4est_lid_t * result);
```
