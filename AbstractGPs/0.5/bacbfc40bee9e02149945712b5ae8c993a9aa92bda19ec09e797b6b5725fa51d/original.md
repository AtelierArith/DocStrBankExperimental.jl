```
logpdf(f::FiniteGP, y::AbstractVecOrMat{<:Real})
```

The logpdf of `y` under `f` if `y isa AbstractVector`. The logpdf of each column of `y` if `y isa Matrix`.

```jldoctest
julia> f = GP(Matern32Kernel());

julia> x = randn(11);

julia> y = rand(f(x));

julia> logpdf(f(x), y) isa Real
true

julia> Y = rand(f(x), 3);

julia> logpdf(f(x), Y) isa AbstractVector{<:Real}
true
```
