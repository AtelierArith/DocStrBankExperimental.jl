```
logitcrossentropy(ŷ, y; dims = 1, agg = mean)
```

Return the cross entropy calculated by

```
agg(-sum(y .* logsoftmax(ŷ; dims); dims))
```

This is mathematically equivalent to `crossentropy(softmax(ŷ), y)`, but is more numerically stable than using functions [`crossentropy`](@ref) and [softmax](@ref Softmax) separately.

See also: [`binarycrossentropy`](@ref), [`logitbinarycrossentropy`](@ref), [`label_smoothing`](@ref).

# Example

```jldoctest
julia> y_label = Flux.onehotbatch(collect("abcabaa"), 'a':'c')
3×7 OneHotMatrix(::Vector{UInt32}) with eltype Bool:
 1  ⋅  ⋅  1  ⋅  1  1
 ⋅  1  ⋅  ⋅  1  ⋅  ⋅
 ⋅  ⋅  1  ⋅  ⋅  ⋅  ⋅

julia> y_model = reshape(vcat(-9:0, 0:9, 7.5f0), 3, 7)
3×7 Matrix{Float32}:
 -9.0  -6.0  -3.0  0.0  2.0  5.0  8.0
 -8.0  -5.0  -2.0  0.0  3.0  6.0  9.0
 -7.0  -4.0  -1.0  1.0  4.0  7.0  7.5

julia> Flux.logitcrossentropy(y_model, y_label)
1.5791205f0

julia> Flux.crossentropy(softmax(y_model), y_label)
1.5791197f0
```
