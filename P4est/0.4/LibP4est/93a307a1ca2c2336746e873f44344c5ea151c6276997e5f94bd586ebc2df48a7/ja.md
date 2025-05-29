```
sc_uint128_sub_inplace(a, b)
```

uint128*t *b* を uint128*t *a* から引きます。結果は *a* に保存されます。*a* == *b* は許可されています。この関数は、結果が >= 0 であることを前提としています。

### パラメータ

  * `a`:[in,out] [`sc_uint128_t`](@ref) へのポインタ。*a* は *a* - *b* によって上書きされます。
  * `b`:[in] [`sc_uint128_t`](@ref) へのポインタ。

### プロトタイプ

```c
void sc_uint128_sub_inplace (sc_uint128_t * a, const sc_uint128_t * b);
```
