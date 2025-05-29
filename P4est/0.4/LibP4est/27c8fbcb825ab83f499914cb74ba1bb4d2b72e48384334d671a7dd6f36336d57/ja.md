```
p8est_lid_compare(a, b)
```

[`p8est_lid_t`](@ref) *a* と [`p8est_lid_t`](@ref) *b* を比較します。

### パラメータ

  * `a`:[in] [`p8est_lid_t`](@ref) へのポインタ。
  * `b`:[in] [`p8est_lid_t`](@ref) へのポインタ。

### 戻り値

a < b の場合は -1、a > b の場合は 1、a == b の場合は 0 を返します。

### プロトタイプ

```c
int p8est_lid_compare (const p8est_lid_t * a, const p8est_lid_t * b);
```
