```
sc_uint128_bitwise_or_inplace(a, b)
```

uint128*t *a* と uint128*t *b* のビット単位の論理和を計算します。 *a* == *b* は許可されています。

### パラメータ

  * `a`:[in,out] [`sc_uint128_t`](@ref) へのポインタ。ビット単位の論理和は *a* に保存されます。
  * `b`:[in] [`sc_uint128_t`](@ref) へのポインタ。

### プロトタイプ

```c
void sc_uint128_bitwise_or_inplace (sc_uint128_t * a, const sc_uint128_t * b);
```
