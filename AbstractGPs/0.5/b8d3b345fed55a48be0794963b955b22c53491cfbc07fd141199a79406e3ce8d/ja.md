```
mean(fx::FiniteGP)
```

`fx`の平均ベクトルを計算します。

```jldoctest
julia> f = GP(Matern52Kernel());

julia> x = randn(11);

julia> mean(f(x)) == zeros(11)
true
```
