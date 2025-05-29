```
sc_uint128_sub(a, b, result)
```

uint128*t *b* を uint128*t *a* から引きます。この関数は、結果が >= 0 であることを前提としています。 *result* == *a* または *result* == *b* は許可されていません。 *a* == *b* は許可されています。

### パラメータ

  * `a`:[in] [`sc_uint128_t`](@ref) へのポインタ。
  * `b`:[in] [`sc_uint128_t`](@ref) へのポインタ。
  * `result`:[out] [`sc_uint128_t`](@ref) へのポインタ。差 *a* - *b* は *result* に保存されます。

### プロトタイプ

```c
void sc_uint128_sub (const sc_uint128_t * a, const sc_uint128_t * b, sc_uint128_t * result);
```
