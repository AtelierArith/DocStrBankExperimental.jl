```
is_generator(g::Integer, q::Integer, factors::Array) -> Bool
```

`g`が`Z_q`の生成元である場合にtrueを返します。ここで、`q`は素数であり、`factors`は`q - 1 = p1^e1 * p2^e2 ... * pk^ek`の素因数分解です。

```
q = 2^7 * 5 + 1
is_generator(2, q, [2, 5]) -> false
is_generator(3, q, [2, 5]) -> true
```
