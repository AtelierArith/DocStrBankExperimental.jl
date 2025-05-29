```
sc_uint128_compare(a, b)
```

[`sc_uint128_t`](@ref) *a* と [`sc_uint128_t`](@ref) *b* を比較します。

### パラメータ

  * `a`:[in] [`sc_uint128_t`](@ref) へのポインタ。
  * `b`:[in] [`sc_uint128_t`](@ref) へのポインタ。

### 戻り値

a < b の場合は -1、a > b の場合は 1、a == b の場合は 0 を返します。

### プロトタイプ

```c
int sc_uint128_compare (const void *a, const void *b);
```
