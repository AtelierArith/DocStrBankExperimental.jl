```
sc_uint128_is_equal(a, b)
```

[`sc_uint128_t`](@ref) *a* と [`sc_uint128_t`](@ref) *b* が等しいかどうかをチェックします。

### パラメータ

  * `a`:[in] [`sc_uint128_t`](@ref) へのポインタ。
  * `b`:[in] [`sc_uint128_t`](@ref) へのポインタ。

### 戻り値

*a* と *b* が等しい場合は真の値を返し、そうでない場合は偽を返します。

### プロトタイプ

```c
int sc_uint128_is_equal (const sc_uint128_t * a, const sc_uint128_t * b);
```
