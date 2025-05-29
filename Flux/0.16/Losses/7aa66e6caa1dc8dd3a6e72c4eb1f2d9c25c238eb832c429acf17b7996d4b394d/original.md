```
focal_loss(ŷ, y; dims=1, agg=mean, gamma=2, eps=eps(eltype(ŷ)))
```

Return the [focal_loss](https://arxiv.org/pdf/1708.02002.pdf) which can be used in classification tasks with highly imbalanced classes. It down-weights well-classified examples and focuses on hard examples. The input, 'ŷ', is expected to be normalized (i.e. [softmax](@ref Softmax) output).

The modulating factor, `γ == gamma`, controls the down-weighting strength. For `γ == 0`, the loss is mathematically equivalent to [`Losses.crossentropy`](@ref).

# Example

```jldoctest
julia> y = [1  0  0  0  1
            0  1  0  1  0
            0  0  1  0  0]
3×5 Matrix{Int64}:
 1  0  0  0  1
 0  1  0  1  0
 0  0  1  0  0

julia> ŷ = softmax(reshape(-7:7, 3, 5) .* 1f0)
3×5 Matrix{Float32}:
 0.0900306  0.0900306  0.0900306  0.0900306  0.0900306
 0.244728   0.244728   0.244728   0.244728   0.244728
 0.665241   0.665241   0.665241   0.665241   0.665241

julia> Flux.focal_loss(ŷ, y) ≈ 1.1277571935622628
true
```

See also: [`Losses.binary_focal_loss`](@ref) for binary (not one-hot) labels
