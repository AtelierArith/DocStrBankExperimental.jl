```
crt(a, b, p, q)
```

Given `0 <= a < p` and `0 <= b < q` with `a == b mod(gcd(p, q)` return unique solution `x ≡ a mod p` and `x ≡ b mod q` with `0 <= x < lcm(p, q)`.

Return `x, lcm(p, q)`.
