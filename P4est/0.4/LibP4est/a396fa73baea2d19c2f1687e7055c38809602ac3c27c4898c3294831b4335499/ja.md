```
sc_uint128_add_inplace(a, b)
```

uint128 *b* を uint128_t *a* に加算します。結果は *a* に保存されます。*a* == *b* は許可されています。

### パラメータ

  * `a`:[in,out] [`sc_uint128_t`](@ref) へのポインタ。*a* は *a* + *b* によって上書きされます。
  * `b`:[in] [`sc_uint128_t`](@ref) へのポインタ。

### プロトタイプ

```c
void sc_uint128_add_inplace (sc_uint128_t * a, const sc_uint128_t * b);
```
