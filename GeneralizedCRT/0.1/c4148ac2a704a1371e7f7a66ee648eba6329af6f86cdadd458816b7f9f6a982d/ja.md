```
crt(a, b, p, q)
```

`0 <= a < p` および `0 <= b < q` で `a == b mod(gcd(p, q)` の場合、`x ≡ a mod p` および `x ≡ b mod q` の一意の解を返します。条件は `0 <= x < lcm(p, q)` です。

`x, lcm(p, q)` を返します。
