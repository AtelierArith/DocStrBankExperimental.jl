```
binarycrossentropy(ŷ, y; agg = mean, eps = eps(eltype(ŷ)))
```

Return the binary cross-entropy loss, computed as

```
agg(@.(-y * log(ŷ + ϵ) - (1 - y) * log(1 - ŷ + ϵ)))
```

Where typically, the prediction `ŷ` is given by the output of a [sigmoid](@ref man-activations) activation. The `ϵ == eps` term is included to avoid infinity. Using [`logitbinarycrossentropy`](@ref) is recomended over `binarycrossentropy` for numerical stability.

Use [`label_smoothing`](@ref) to smooth the `y` value as preprocessing before computing the loss.

See also: [`crossentropy`](@ref), [`logitcrossentropy`](@ref).

# Examples

```jldoctest
julia> y_bin = Bool[1,0,1]
3-element Vector{Bool}:
 1
 0
 1

julia> y_prob = softmax(reshape(vcat(1:3, 3:5), 2, 3) .* 1f0)
2×3 Matrix{Float32}:
 0.268941  0.5  0.268941
 0.731059  0.5  0.731059

julia> Flux.binarycrossentropy(y_prob[2,:], y_bin)
0.43989f0

julia> all(p -> 0 < p < 1, y_prob[2,:])  # else DomainError
true

julia> y_hot = Flux.onehotbatch(y_bin, 0:1)
2×3 OneHotMatrix(::Vector{UInt32}) with eltype Bool:
 ⋅  1  ⋅
 1  ⋅  1

julia> Flux.crossentropy(y_prob, y_hot)
0.43989f0
```
