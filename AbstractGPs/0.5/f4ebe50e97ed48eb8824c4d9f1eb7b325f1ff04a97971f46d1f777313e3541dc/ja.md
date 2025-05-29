```
mean_and_cov(f::FiniteGP)
```

`(mean(f), cov(f))` と同等ですが、時には別々に計算するよりも一緒に計算する方が効率的です。

```jldoctest
julia> fx = GP(SqExponentialKernel())(range(-3.0, 3.0; length=10), 0.1);

julia> mean_and_cov(fx) == (mean(fx), cov(fx))
true
```
