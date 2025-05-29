```
crossentropy(ŷ, y; dims = 1, eps = eps(eltype(ŷ)), agg = mean)
```

Return the cross entropy between the given probability distributions; calculated as

```
agg(-sum(y .* log.(ŷ .+ ϵ); dims))
```

Cross entropy is typically used as a loss in multi-class classification, in which case the labels `y` are given in a one-hot format. `dims` specifies the dimension (or the dimensions) containing the class probabilities. The prediction `ŷ` is supposed to sum to one across `dims`, as would be the case with the output of a [softmax](@ref Softmax) operation.

For numerical stability, it is recommended to use [`logitcrossentropy`](@ref) rather than `softmax` followed by `crossentropy` .

Use [`label_smoothing`](@ref) to smooth the true labels as preprocessing before computing the loss.

See also: [`logitcrossentropy`](@ref), [`binarycrossentropy`](@ref), [`logitbinarycrossentropy`](@ref).

# Example

```jldoctest
julia> y_label = Flux.onehotbatch([0, 1, 2, 1, 0], 0:2)
3×5 OneHotMatrix(::Vector{UInt32}) with eltype Bool:
 1  ⋅  ⋅  ⋅  1
 ⋅  1  ⋅  1  ⋅
 ⋅  ⋅  1  ⋅  ⋅

julia> y_model = softmax(reshape(-7:7, 3, 5) .* 1f0)
3×5 Matrix{Float32}:
 0.0900306  0.0900306  0.0900306  0.0900306  0.0900306
 0.244728   0.244728   0.244728   0.244728   0.244728
 0.665241   0.665241   0.665241   0.665241   0.665241

julia> sum(y_model; dims=1)
1×5 Matrix{Float32}:
 1.0  1.0  1.0  1.0  1.0

julia> Flux.crossentropy(y_model, y_label)
1.6076053f0

julia> 5 * ans ≈ Flux.crossentropy(y_model, y_label; agg=sum)
true

julia> y_smooth = Flux.label_smoothing(y_label, 0.15f0)
3×5 Matrix{Float32}:
 0.9   0.05  0.05  0.05  0.9
 0.05  0.9   0.05  0.9   0.05
 0.05  0.05  0.9   0.05  0.05

julia> Flux.crossentropy(y_model, y_smooth)
1.5776052f0
```
