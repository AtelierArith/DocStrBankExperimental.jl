```
mean_and_cov(f::AbstractGP, x::AbstractVector)
```

`mean(f(x))` と `cov(f(x))` の両方を計算します。特に事後分布の場合、別々に計算するよりも効率的なことがあります。
