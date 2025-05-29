```
softmax(x; dims = 1)
```

[Softmax](https://en.wikipedia.org/wiki/Softmax_function) turns input array `x` into probability distributions that sum to 1 along the dimensions specified by `dims`. It is semantically equivalent to the following:

```
softmax(x; dims = 1) = exp.(x) ./ sum(exp.(x), dims = dims)
```

with additional manipulations enhancing numerical stability.

For a matrix input `x` it will by default (`dims = 1`) treat it as a batch of vectors, with each column independent. Keyword `dims = 2` will instead treat rows independently, and so on.

See also [`logsoftmax`](@ref).

# Examples

```jldoctest; filter = r"[+-]?([0-9]*[.])?[0-9]+(f[+-]*[0-9])?"
julia> softmax([1, 2, 3])
3-element Vector{Float64}:
 0.09003057317038046
 0.24472847105479764
 0.6652409557748218

julia> softmax([1 2 3; 2 2 2])  # dims=1
2×3 Matrix{Float64}:
 0.268941  0.5  0.731059
 0.731059  0.5  0.268941

julia> softmax([1 2 3; 2 2 2]; dims=2)
2×3 Matrix{Float64}:
 0.0900306  0.244728  0.665241
 0.333333   0.333333  0.333333
```

Note that, when used with Flux.jl, `softmax` must not be passed to layers like `Dense` which accept an activation function. The activation is broadcasted over the result, thus applies to individual numbers. But `softmax` always needs to see the whole column.

```julia-repl
julia> using Flux

julia> x = randn(Float32, 4, 4, 3, 13);

julia> model = Chain(Conv((4, 4), 3 => 8, tanh), Flux.flatten, Dense(8 => 7), softmax);

julia> model(x) |> size
(7, 13)

julia> Dense(4 => 7, softmax)(x)
ERROR: `softmax(x)` called with a number, but it expects an array. 
```
