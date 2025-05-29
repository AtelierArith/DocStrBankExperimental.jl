```
binary_focal_loss(ŷ, y; agg=mean, gamma=2, eps=eps(eltype(ŷ)))
```

Return the [binary*focal*loss](https://arxiv.org/pdf/1708.02002.pdf) The input, 'ŷ', is expected to be normalized (i.e. [softmax](@ref Softmax) output).

For `gamma = 0`, the loss is mathematically equivalent to [`Losses.binarycrossentropy`](@ref).

See also: [`Losses.focal_loss`](@ref) for multi-class setting

# Example

```jldoctest
julia> y = [0  1  0
            1  0  1]
2×3 Matrix{Int64}:
 0  1  0
 1  0  1

julia> ŷ = [0.268941  0.5  0.268941
            0.731059  0.5  0.731059]
2×3 Matrix{Float64}:
 0.268941  0.5  0.268941
 0.731059  0.5  0.731059

julia> Flux.binary_focal_loss(ŷ, y) ≈ 0.0728675615927385
true
```
