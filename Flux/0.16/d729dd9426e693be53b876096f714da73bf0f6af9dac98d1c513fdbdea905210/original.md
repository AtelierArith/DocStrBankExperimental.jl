```
GroupNorm(channels::Int, G::Int, λ = identity;
          initβ = zeros32,
          initγ = ones32,
          affine = true,
          eps = 1f-5,
          momentum = 0.1f0)
```

[Group Normalization](https://arxiv.org/abs/1803.08494) layer.

`chs` is the number of channels, the channel dimension of your input. For an array of N dimensions, the `N-1`th index is the channel dimension.

`G` is the number of groups along which the statistics are computed. The number of channels must be an integer multiple of the number of groups.

`channels` should be the size of the channel dimension in your data (see below).

Given an array with `N > 2` dimensions, call the `N-1`th the channel dimension. For `WHCN` images it's the usual channel dimension.

If `affine=true`, it also applies  a shift and a rescale to the input through to learnable per-channel bias `β` and scale `γ` parameters.

# Examples

```jldoctest
julia> using Statistics

julia> xs = rand(3, 3, 4, 2);  # a batch of 2 images, each having 4 channels

julia> m = GroupNorm(4, 2);

julia> y = m(xs);

julia> isapprox(std(y[:, :, 1:2, 1]), 1, atol=0.1) && std(xs[:, :, 1:2, 1]) != std(y[:, :, 1:2, 1])
true

julia> isapprox(std(y[:, :, 3:4, 2]), 1, atol=0.1) && std(xs[:, :, 3:4, 2]) != std(y[:, :, 3:4, 2])
true
```
