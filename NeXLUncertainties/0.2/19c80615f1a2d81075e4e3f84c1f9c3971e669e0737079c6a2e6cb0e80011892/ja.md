```
divide(n::UncertainValue, d::UncertainValue, cc::AbstractFloat)
```

`n` と `d` が UncertainValue であり、`cc` が相関係数として定義される場合、`n/d` を計算します。ここで、`cc = covar(n,d)/( σ(n), σ(d) )` です。
