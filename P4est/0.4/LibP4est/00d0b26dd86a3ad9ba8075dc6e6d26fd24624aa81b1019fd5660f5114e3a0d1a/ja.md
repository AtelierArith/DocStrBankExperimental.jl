```
sc_uint128_bitwise_and(a, b, result)
```

uint128*t *a* と uint128*t *b* のビット単位の AND を計算します。 *a* == *result* は許可されています。さらに、 *a* == *result* および/または *b* == *result* も許可されています。

### パラメータ

  * `a`:[in] [`sc_uint128_t`](@ref) へのポインタ。
  * `b`:[in] [`sc_uint128_t`](@ref) へのポインタ。
  * `result`:[out] [`sc_uint128_t`](@ref) へのポインタ。 *a* と *b* のビット単位の AND が *result* に保存されます。

### プロトタイプ

```c
void sc_uint128_bitwise_and (const sc_uint128_t * a, const sc_uint128_t * b, sc_uint128_t * result);
```
