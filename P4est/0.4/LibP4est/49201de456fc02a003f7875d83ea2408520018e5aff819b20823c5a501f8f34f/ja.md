```
sc_uint128_init(a, high, low)
```

与えられた値に対して符号なし128ビット整数を初期化します。

### パラメータ

  * `a`:[in,out] 初期化される[`sc_uint128_t`](@ref)へのポインタ。
  * `high`:[in] *a*を初期化するための与えられた高位ビット。
  * `low`:[in] *a*を初期化するための与えられた低位ビット。

### プロトタイプ

```c
void sc_uint128_init (sc_uint128_t * a, uint64_t high, uint64_t low);
```
