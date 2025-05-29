```
rand!(rng::AbstractRNG, f::FiniteGP, y::AbstractVecOrMat{<:Real})
```

Obtain sample(s) from the marginals `f` using `rng` and write them to `y`.

If `y` is a matrix, then each column corresponds to an independent sample.

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
