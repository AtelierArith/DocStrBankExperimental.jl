```
mean_and_var(f::FiniteGP)
```

`mean(f)` と `cov(f)` の対角要素の両方を計算します。

特に事後分布に対して、別々に計算するよりも効率的な場合があります。

# 例

```jldoctest
julia> fx = GP(SqExponentialKernel())(range(-3.0, 3.0; length=10), 0.1);

julia> mean_and_var(fx) == (mean(fx), var(fx))
true
```
