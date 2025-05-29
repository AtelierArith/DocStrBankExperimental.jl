```
sc_uint128_bitwise_neg(a, result)
```

uint128_t *a*のビット単位の否定を計算します。*a* == *result*は許可されています。

### パラメータ

  * `a`:[in] [`sc_uint128_t`](@ref)へのポインタ。
  * `result`:[out] [`sc_uint128_t`](@ref)へのポインタ。*a*のビット単位の否定が*result*に保存されます。

### プロトタイプ

```c
void sc_uint128_bitwise_neg (const sc_uint128_t * a, sc_uint128_t * result);
```
