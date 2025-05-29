```
crt(a::Vector, m::Vector; nt, splitstreads, splitbinary)
```

与えられた `0 <= a[i] < p[i] for all i` で `a[i] == a[j] mod(gcd(p[i], p[j]) for i != j` の場合、すべての `i` に対して `x ≡ a[i] mod p[i]` の一意の解 `x` を返します。ただし、`0 <= x < lcm(p, q)` です。

オプションの引数: `length(a) > splitthreads=(15)` の場合は `nt=nthreads()` スレッドを使用します。`length(a) > splitbinary=(7)` の場合はバイナリアルゴリズムを使用します。

`x, lcm(p, q)` を返します。
