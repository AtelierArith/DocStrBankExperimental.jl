```
stirling2( n :: Int64, k :: Int64  ) :: Int64
```

Counts the number of ways to partition `n` items into `k` unlabelled groups. This quantity is known as Stirling's number of the 2nd kind:

$$
\left\{n \atop k \right\} = \frac{1}{k!}\sum_{i=0}^k (-1)^i\binom{k}{i}(k-i)^n
$$

Throws a `DomainError` if inputs do not satisfy `n ≥ k ≥ 1`.
