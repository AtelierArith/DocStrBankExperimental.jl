```
BatchNorm(channels::Integer, λ=identity;
          initβ=zeros32, initγ=ones32,
          affine=true, track_stats=true, active=nothing,
          eps=1f-5, momentum= 0.1f0)
```

[Batch Normalization](https://arxiv.org/abs/1502.03167) layer. `channels` should be the size of the channel dimension in your data (see below).

Given an array with `N` dimensions, call the `N-1`th the channel dimension. For a batch of feature vectors this is just the data dimension, for `WHCN` images it's the usual channel dimension.

`BatchNorm` computes the mean and variance for each `D_1×...×D_{N-2}×1×D_N` input slice and normalises the input accordingly.

If `affine=true`, it also applies  a shift and a rescale to the input through to learnable per-channel bias β and scale γ parameters.

After normalisation, elementwise activation `λ` is applied.

If `track_stats=true`, accumulates mean and var statistics in training phase that will be used to renormalize the input in test phase.

Use [`testmode!`](@ref) during inference.

# Examples

```julia-repl
julia> using Statistics

julia> xs = rand(3, 3, 3, 2);  # a batch of 2 images, each having 3 channels

julia> m = BatchNorm(3);

julia> Flux.trainmode!(m);

julia> isapprox(std(m(xs)), 1, atol=0.1) && std(xs) != std(m(xs))
true
```
