```
P2Quantile(τ = 0.5)
```

P^2アルゴリズムを使用して近似分位数を計算します。これは[`Quantile`](@ref)で使用されるアルゴリズムよりも計算コストが高いですが、より正確です。

参照: [https://www.cse.wustl.edu/~jain/papers/ftp/psqr.pdf](https://www.cse.wustl.edu/~jain/papers/ftp/psqr.pdf)

# 例

```
fit!(P2Quantile(.5), rand(10^5))
```
