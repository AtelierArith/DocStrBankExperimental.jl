```
add(ka::Real, a::UncertainValue, kb::Real, b::UncertainValue, cc::AbstractFloat)
```

`ka*a + kb*b` を計算します。ここで `a` と `b` は UncertainValue であり、`cc` は `cc = covar(a,b)/( σ(a), σ(b) )` と定義される相関係数です。
