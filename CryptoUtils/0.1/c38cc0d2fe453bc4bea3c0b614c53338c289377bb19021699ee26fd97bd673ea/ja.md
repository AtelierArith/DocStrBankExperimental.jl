```
get_safe_prime_generator(q::BigInt) -> BigInt
```

`q = 2 * p + 1` で `q, p` が素数であるとき、`Z_q` の生成器を返します。
