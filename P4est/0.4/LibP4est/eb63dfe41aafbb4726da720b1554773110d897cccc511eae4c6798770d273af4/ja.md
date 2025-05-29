```
p8est_lid_is_equal(a, b)
```

[`p8est_lid_t`](@ref) *a* と [`p8est_lid_t`](@ref) *b* が等しいかどうかをチェックします。

### パラメータ

  * `a`:[in] [`p8est_lid_t`](@ref) へのポインタ。
  * `b`:[in] [`p8est_lid_t`](@ref) へのポインタ。

### 戻り値

*a* と *b* が等しい場合は真の値を返し、そうでない場合は偽を返します。

### プロトタイプ

```c
int p8est_lid_is_equal (const p8est_lid_t * a, const p8est_lid_t * b);
```
