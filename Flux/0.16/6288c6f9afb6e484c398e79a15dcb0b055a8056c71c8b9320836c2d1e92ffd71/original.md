```
AlphaDropout(p; [rng, active])
```

A dropout layer. Used in [Self-Normalizing Neural Networks](https://arxiv.org/abs/1706.02515). The AlphaDropout layer ensures that mean and variance of activations remain the same as before.

Does nothing to the input once [`testmode!`](@ref) is true.

# Examples

```jldoctest
julia> using Statistics

julia> x = randn32(1000,1);

julia> m = Chain(Dense(1000 => 1000, selu), AlphaDropout(0.2));

julia> Flux.trainmode!(m);

julia> y = m(x);

julia> isapprox(std(x), std(y), atol=0.2)
true
```
