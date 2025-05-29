```
update!(opt_state, model_grad::Duplicated)
```

For use with Enzyme's `Duplicated`, which holds both a model/parameters and the corresponding gradient.

# Example

```jldoctest
julia> using Optimisers, EnzymeCore

julia> x_dx = Duplicated(Float16[1,2,3], Float16[1,0,-4])
Duplicated{Vector{Float16}}(Float16[1.0, 2.0, 3.0], Float16[1.0, 0.0, -4.0])

julia> st = Optimisers.setup(Momentum(1/9), x_dx)  # acts only on x not on dx
Leaf(Momentum(0.111111, 0.9), Float16[0.0, 0.0, 0.0])

julia> Optimisers.update!(st, x_dx)  # mutates both arguments

julia> x_dx
Duplicated{Vector{Float16}}(Float16[0.8887, 2.0, 3.445], Float16[1.0, 0.0, -4.0])

julia> st
Leaf(Momentum(0.111111, 0.9), Float16[0.1111, 0.0, -0.4443])
```
