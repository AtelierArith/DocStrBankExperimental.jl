```
sc_uint128_add(a, b, result)
```

uint128*t *b* を uint128*t *a* に加算します。 *result* == *a* または *result* == *b* は許可されていません。 *a* == *b* は許可されています。

### パラメータ

  * `a`:[in] [`sc_uint128_t`](@ref) へのポインタ。
  * `b`:[in] [`sc_uint128_t`](@ref) へのポインタ。
  * `result`:[out] [`sc_uint128_t`](@ref) へのポインタ。合計 *a* + *b* が *result* に保存されます。

### プロトタイプ

```c
void sc_uint128_add (const sc_uint128_t * a, const sc_uint128_t * b, sc_uint128_t * result);
```
