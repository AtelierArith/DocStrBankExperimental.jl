```
label_smoothing(y::Union{Number, AbstractArray}, α; dims::Int=1)
```

Returns smoothed labels, meaning the confidence on label values are relaxed.

When `y` is given as one-hot vector or batch of one-hot, its calculated as

```
y .* (1 - α) .+ α / size(y, dims)
```

when `y` is given as a number or batch of numbers for binary classification, its calculated as

```
y .* (1 - α) .+ α / 2
```

in which case the labels are squeezed towards `0.5`.

α is a number in interval (0, 1) called the smoothing factor. Higher the value of α larger the smoothing of `y`.

`dims` denotes the one-hot dimension, unless `dims=0` which denotes the application of label smoothing to binary distributions encoded in a single number.

# Example

```jldoctest
julia> y = Flux.onehotbatch([1, 1, 1, 0, 1, 0], 0:1)
2×6 OneHotMatrix(::Vector{UInt32}) with eltype Bool:
 ⋅  ⋅  ⋅  1  ⋅  1
 1  1  1  ⋅  1  ⋅

julia> y_smoothed = Flux.label_smoothing(y, 0.2f0)
2×6 Matrix{Float32}:
 0.1  0.1  0.1  0.9  0.1  0.9
 0.9  0.9  0.9  0.1  0.9  0.1

julia> y_sim = softmax(y .* log(2f0))
2×6 Matrix{Float32}:
 0.333333  0.333333  0.333333  0.666667  0.333333  0.666667
 0.666667  0.666667  0.666667  0.333333  0.666667  0.333333

julia> y_dis = vcat(y_sim[2,:]', y_sim[1,:]')
2×6 Matrix{Float32}:
 0.666667  0.666667  0.666667  0.333333  0.666667  0.333333
 0.333333  0.333333  0.333333  0.666667  0.333333  0.666667

julia> Flux.crossentropy(y_sim, y) < Flux.crossentropy(y_sim, y_smoothed)
true

julia> Flux.crossentropy(y_dis, y) > Flux.crossentropy(y_dis, y_smoothed)
true
```
