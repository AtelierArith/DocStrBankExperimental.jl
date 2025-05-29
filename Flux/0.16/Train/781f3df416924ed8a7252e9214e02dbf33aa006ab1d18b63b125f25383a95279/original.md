```
opt_state = setup(rule, model)
```

This is a version of `Optimisers.setup`, and is the first step before using [`train!`](@ref Flux.train!). It differs from `Optimisers.setup` in that it:

  * has one extra check for mutability (since Flux expects to mutate the model in-place, while Optimisers.jl is designed to return an updated model)
  * has methods which accept Flux's old optimisers, and convert them. (The old `Flux.Optimise.Adam` and new `Optimisers.Adam` are distinct types.)

# Example

```jldoctest
julia> model = Dense(2 => 1, leakyrelu; init=ones);

julia> opt_state = Flux.setup(Momentum(0.1), model)  # this encodes the optimiser and its state
(weight = Leaf(Momentum(0.1, 0.9), [0.0 0.0]), bias = Leaf(Momentum(0.1, 0.9), [0.0]), σ = ())

julia> x1, y1 = [0.2, -0.3], [0.4];  # use the same data for two steps:

julia> Flux.train!(model, [(x1, y1), (x1, y1)], opt_state) do m, x, y
         sum(abs.(m(x) .- y)) * 100
       end

julia> model.bias  # was zero, mutated by Flux.train!
1-element Vector{Float64}:
 10.19

julia> opt_state  # mutated by Flux.train!
(weight = Leaf(Momentum(0.1, 0.9), [-2.018 3.027]), bias = Leaf(Momentum(0.1, 0.9), [-10.09]), σ = ())
```
