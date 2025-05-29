```
p4est_lid_bitwise_and(a, b, result)
```

uint128*t *a* と uint128*t *b* のビット単位の AND を計算します。 *a* == *result* は許可されています。さらに、 *a* == *result* および/または *b* == *result* も許可されています。

### パラメータ

  * `a`:[in] [`p4est_lid_t`](@ref) へのポインタ。
  * `b`:[in] [`p4est_lid_t`](@ref) へのポインタ。
  * `result`:[out] [`p4est_lid_t`](@ref) へのポインタ。 *a* と *b* のビット単位の AND が *result* に保存されます。

### プロトタイプ

```c
void p4est_lid_bitwise_and (const p4est_lid_t * a, const p4est_lid_t * b, p4est_lid_t * result);
```
