```
multiply(a::UncertainValue, b::UncertainValue, cc::AbstractFloat)
```

`a`と`b`がUncertainValueであり、`cc`が`cc = covar(a,b)/( σ(a), σ(b) )`として定義される相関係数である場合、`a*b`を計算します。
