```
stirling2( n :: Int64, k :: Int64  ) :: Int64
```

`n` 個のアイテムを `k` 個のラベルのないグループに分割する方法の数をカウントします。この量は第2種のスターリング数として知られています：

$$
\left\{n \atop k \right\} = \frac{1}{k!}\sum_{i=0}^k (-1)^i\binom{k}{i}(k-i)^n
$$

`n ≥ k ≥ 1` の条件を満たさない場合、`DomainError` をスローします。
