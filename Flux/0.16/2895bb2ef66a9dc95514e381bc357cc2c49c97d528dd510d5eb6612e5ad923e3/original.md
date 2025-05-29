```
state(x)
```

Return an object with the same nested structure as `x` according to `Functors.children`,  but made only of basic containers (e.g. named tuples, tuples, arrays, and dictionaries).

Besides trainable and non-trainable arrays, the state will contain leaf nodes that are not arrays, such as numbers, symbols, strings, and nothing values. The leaf types that end up in the state could increase in the future.

This method is particularly useful for saving and loading models,  since the state contain only simple data types that can be easily serialized.

The state can be passed to [`loadmodel!`](@ref) to restore the model.

# Examples

## Copy the state into another model

```jldoctest
julia> m1 = Chain(Dense(1, 2, tanh; init=ones), Dense(2, 1; init=ones));

julia> s = Flux.state(m1)
(layers = ((weight = [1.0; 1.0;;], bias = [0.0, 0.0], σ = ()), (weight = [1.0 1.0], bias = [0.0], σ = ())),)

julia> m2 = Chain(Dense(1, 2, tanh), Dense(2, 1; bias=false));  # weights are random numbers

julia> Flux.loadmodel!(m2, s);

julia> m2[1].weight   # now the weights of m2 are the same as m1
2×1 Matrix{Float32}:
 1.0
 1.0

julia> Flux.state(trainmode!(Dropout(0.2)))  # contains p & activity, but not RNG state
(p = 0.2, dims = (), active = true, rng = ())

julia> Flux.state(BatchNorm(1))  # contains non-trainable arrays μ, σ²
(λ = (), β = Float32[0.0], γ = Float32[1.0], μ = Float32[0.0], σ² = Float32[1.0], ϵ = 1.0f-5, momentum = 0.1f0, affine = true, track_stats = true, active = nothing, chs = 1)
```

## Save and load with BSON

```julia-repl
julia> using BSON

julia> BSON.@save "checkpoint.bson" model_state = s

julia> Flux.loadmodel!(m2, BSON.load("checkpoint.bson")[:model_state])
```

## Save and load with JLD2

```julia-repl
julia> using JLD2

julia> JLD2.jldsave("checkpoint.jld2", model_state = s)

julia> Flux.loadmodel!(m2, JLD2.load("checkpoint.jld2", "model_state"))
```
