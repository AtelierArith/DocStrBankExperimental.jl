```
rand(rng::AbstractRNG, f::FiniteGP, N::Int=1)
```

`rng`を使用して、`f`の周辺から`N`個の独立サンプルを取得します。単一サンプルメソッドは`length(f)`のベクトルを生成します。マルチサンプルメソッドは`length(f)` × `N`の`Matrix`を生成します。

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
