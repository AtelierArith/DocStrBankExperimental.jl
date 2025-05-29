```
binomial(n::ZZRingElem, k::ZZRingElem)
```

二項係数 $\frac{n (n-1) \cdots (n-k+1)}{k!}$ を返します。もし $k < 0$ の場合は $0$ を返し、整数 `n` と `k` に対して恒常的に成り立つ恒等式 `binomial(n, k) == binomial(n - 1, k - 1) + binomial(n - 1, k)` があります。
