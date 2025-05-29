```
Dense(in => out, σ=identity; bias=true, init=glorot_uniform)
Dense(W::AbstractMatrix, [bias, σ])
```

Create a traditional fully connected layer, whose forward pass is given by:

```
y = σ.(W * x .+ bias)
```

The input `x` should be a vector of length `in`, or batch of vectors represented as an `in × N` matrix, or any array with `size(x,1) == in`. The out `y` will be a vector  of length `out`, or a batch with `size(y) == (out, size(x)[2:end]...)`

Keyword `bias=false` will switch off trainable bias for the layer. The initialisation of the weight matrix is `W = init(out, in)`, calling the function given to keyword `init`, with default [`glorot_uniform`](@ref Flux.glorot_uniform). The weight matrix and/or the bias vector (of length `out`) may also be provided explicitly.

# Examples

```jldoctest
julia> model = Dense(5 => 2)
Dense(5 => 2)       # 12 parameters

julia> model(rand32(5, 64)) |> size
(2, 64)

julia> model(rand32(5, 6, 4, 64)) |> size  # treated as three batch dimensions
(2, 6, 4, 64)

julia> model2 = Dense(ones(2, 5), false, tanh)  # using provided weight matrix
Dense(5 => 2, tanh; bias=false)  # 10 parameters

julia> model2(ones(5))
2-element Vector{Float64}:
 0.9999092042625951
 0.9999092042625951

julia> Flux.trainables(model2)  # no trainable bias
1-element Vector{AbstractArray}:
 [1.0 1.0 … 1.0 1.0; 1.0 1.0 … 1.0 1.0]
```
