```
InstanceNorm(channels::Integer, λ=identity;
             initβ=zeros32, initγ=ones32,
             affine=false, track_stats=false,
             eps=1f-5, momentum=0.1f0)
```

[Instance Normalization](https://arxiv.org/abs/1607.08022) layer. `channels` should be the size of the channel dimension in your data (see below).

Given an array with `N > 2` dimensions, call the `N-1`th the channel dimension. For `WHCN` images it's the usual channel dimension.

`InstanceNorm` computes the mean and variance for each `D_1×...×D_{N-2}×1×1` input slice and normalises the input accordingly.

If `affine=true`, it also applies  a shift and a rescale to the input through to learnable per-channel bias `β` and scale `γ` parameters.

If `track_stats=true`, accumulates mean and var statistics in training phase that will be used to renormalize the input in test phase.

**Warning**: the defaults for `affine` and `track_stats` used to be `true` in previous Flux versions (< v0.12).

# Examples

```jldoctest
julia> using Statistics

julia> xs = rand(3, 3, 3, 2);  # a batch of 2 images, each having 3 channels

julia> m = InstanceNorm(3);

julia> y = m(xs);

julia> isapprox(std(y, dims=1:2), ones(1, 1, 3, 2), atol=0.2) && std(y, dims=1:2) != std(xs, dims=1:2)
true
```
