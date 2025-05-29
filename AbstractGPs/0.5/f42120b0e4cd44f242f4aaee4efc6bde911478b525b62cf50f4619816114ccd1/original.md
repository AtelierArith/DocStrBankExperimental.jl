```
rand(rng::AbstractRNG, f::FiniteGP, N::Int=1)
```

Obtain `N` independent samples from the marginals `f` using `rng`. Single-sample methods produce a `length(f)` vector. Multi-sample methods produce a `length(f)` × `N` `Matrix`.

```jldoctest
julia> f = GP(Matern32Kernel());

julia> x = randn(11);

julia> rand(f(x)) isa Vector{Float64}
true

julia> rand(MersenneTwister(123456), f(x)) isa Vector{Float64}
true

julia> rand(f(x), 3) isa Matrix{Float64}
true

julia> rand(MersenneTwister(123456), f(x), 3) isa Matrix{Float64}
true
```
