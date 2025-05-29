```
rand!(rng::AbstractRNG, f::FiniteGP, y::AbstractVecOrMat{<:Real})
```

マージナル `f` からサンプルを取得し、`rng` を使用して `y` に書き込みます。

`y` が行列の場合、各列は独立したサンプルに対応します。

```jldoctest
julia> f = GP(Matern32Kernel());

julia> x = randn(11);

julia> y = similar(x);

julia> rand!(f(x), y);

julia> rand!(MersenneTwister(123456), f(x), y);

julia> ys = similar(x, length(x), 3);

julia> rand!(f(x), ys);

julia> rand!(MersenneTwister(123456), f(x), ys);
```
