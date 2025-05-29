```
p4est_lid_compare(a, b)
```

[`p4est_lid_t`](@ref) *a* と [`p4est_lid_t`](@ref) *b* を比較します。

### パラメータ

  * `a`:[in] [`p4est_lid_t`](@ref) へのポインタ。
  * `b`:[in] [`p4est_lid_t`](@ref) へのポインタ。

### 戻り値

a < b の場合は -1、a > b の場合は 1、a == b の場合は 0 を返します。

### プロトタイプ

```c
int p4est_lid_compare (const p4est_lid_t * a, const p4est_lid_t * b);
```
