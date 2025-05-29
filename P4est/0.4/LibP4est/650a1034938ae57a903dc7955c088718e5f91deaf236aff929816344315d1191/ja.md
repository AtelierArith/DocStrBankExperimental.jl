```
sc_uint128_bitwise_and_inplace(a, b)
```

uint128*t *a* と uint128*t *b* のビット単位の AND を計算します。 *a* == *b* は許可されています。

### パラメータ

  * `a`:[in,out] [`sc_uint128_t`](@ref) へのポインタ。ビット単位の AND の結果が *a* に保存されます。
  * `b`:[in] [`sc_uint128_t`](@ref) へのポインタ。

### プロトタイプ

```c
void sc_uint128_bitwise_and_inplace (sc_uint128_t * a, const sc_uint128_t * b);
```
