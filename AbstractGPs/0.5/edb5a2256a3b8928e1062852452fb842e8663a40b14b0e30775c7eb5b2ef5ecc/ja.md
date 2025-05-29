```
marginals(f::FiniteGP)
```

`f`の周辺分布を効率的に表す正規分布のベクトルを計算します。特に、`cov(f(x))`のオフ対角要素は決して計算されません。

```jldoctest
julia> f = GP(Matern32Kernel());

julia> x = randn(11);

julia> fs = marginals(f(x));

julia> mean.(fs) == mean(f(x))
true

julia> std.(fs) == sqrt.(diag(cov(f(x))))
true
```
