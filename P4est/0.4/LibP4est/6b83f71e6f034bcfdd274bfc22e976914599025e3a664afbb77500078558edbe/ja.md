```
sc_uint128_bitwise_or(a, b, result)
```

uint128_t *a* と *b* のビット単位の論理和を計算します。*a* == *result* は許可されています。さらに、*a* == *result* および/または *b* == *result* も許可されています。

### パラメータ

  * `a`:[in] [`sc_uint128_t`](@ref) へのポインタ。
  * `b`:[in] [`sc_uint128_t`](@ref) へのポインタ。
  * `result`:[out] [`sc_uint128_t`](@ref) へのポインタ。*a* と *b* のビット単位の論理和が *result* に保存されます。

### プロトタイプ

```c
void sc_uint128_bitwise_or (const sc_uint128_t * a, const sc_uint128_t * b, sc_uint128_t * result);
```
