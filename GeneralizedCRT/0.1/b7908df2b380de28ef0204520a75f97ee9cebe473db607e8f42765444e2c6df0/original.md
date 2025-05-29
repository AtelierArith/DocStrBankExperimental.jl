```
crt(a::Vector, m::Vector; nt, splitstreads, splitbinary)
```

Given `0 <= a[i] < p[i] for all i` with `a[i] == a[j] mod(gcd(p[i], p[j]) for i != j`, return unique solution `x ≡ a[i] mod p[i] for all i` with `0 <= x < lcm(p, q)`.

Optional arguments: Use `nt=nthreads()` threads if `length(a) > splitthreads=(15)`. Use binary algorithm if `length(a) > splitbinary=(7)`.

Return `x, lcm(p, q)`.
