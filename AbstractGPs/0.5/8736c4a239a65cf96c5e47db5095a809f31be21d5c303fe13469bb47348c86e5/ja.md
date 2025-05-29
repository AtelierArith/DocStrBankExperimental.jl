```
mean_and_var(f::AbstractGP, x::AbstractVector)
```

`mean(f(x))` と `cov(f(x))` の対角要素の両方を計算します。特に事後分布の場合、別々に計算するよりも効率的なことがあります。
