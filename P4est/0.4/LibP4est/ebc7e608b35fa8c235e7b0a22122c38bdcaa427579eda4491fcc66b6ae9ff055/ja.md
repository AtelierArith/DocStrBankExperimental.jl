```
p8est_lid_add_inplace(a, b)
```

[`p8est_lid_t`](@ref) *b* を [`p8est_lid_t`](@ref) *a* に加えます。結果は *a* に保存されます。 *a* == *b* は許可されています。

### パラメータ

  * `a`:[in,out] [`p8est_lid_t`](@ref) へのポインタ。 *a* は *a* + *b* で上書きされます。
  * `b`:[in] [`p8est_lid_t`](@ref) へのポインタ。

### プロトタイプ

```c
void p8est_lid_add_inplace (p8est_lid_t * a, const p8est_lid_t * b);
```
