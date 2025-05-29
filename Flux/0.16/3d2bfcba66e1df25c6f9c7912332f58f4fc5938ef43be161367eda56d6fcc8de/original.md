```
LayerNorm(size..., λ=identity; affine=true, eps=1f-5)
```

A [normalisation layer](https://arxiv.org/abs/1607.06450) designed to be used with recurrent hidden states. The argument `size` should be an integer or a tuple of integers.

In the forward pass, the layer normalises the mean and standard deviation of the input, then applies the elementwise activation `λ`. The input is normalised along the first `length(size)` dimensions for tuple `size`, and along the first dimension for integer `size`. The input is expected to have first dimensions' size equal to `size`.

If `affine=true`, it also applies a learnable shift and rescaling using the [`Scale`](@ref) layer.

See also [`BatchNorm`](@ref), [`InstanceNorm`](@ref), [`GroupNorm`](@ref), and [`normalise`](@ref).

# Examples

```jldoctest
julia> using Statistics

julia> xs = rand(3, 3, 3, 2);  # a batch of 2 images, each having 3 channels

julia> m = LayerNorm(3);

julia> y = m(xs);

julia> isapprox(std(y, dims=1:3), ones(1, 1, 1, 2), atol=0.1) && std(y, dims=1:3) != std(xs, dims=1:3)
true
```
