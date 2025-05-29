```
Optimisers.update!(tree, model, gradient) -> (tree, model)
```

Uses the optimiser and the gradient to change the trainable parameters in the model. Returns the improved model, and the optimiser states needed for the next update. The initial tree of states comes from [`setup`](@ref Optimisers.setup).

This is used in exactly the same manner as [`update`](@ref Optimisers.update), but because it may mutate arrays within the old model (and the old state), it will be faster for models of ordinary `Array`s or `CuArray`s. However, you should not rely on the old model being fully updated but rather use the returned model. (The original state tree is always mutated, as each `Leaf` is mutable.)

# Example

```jldoctest
julia> using StaticArrays, Zygote, Optimisers

julia> m = (x = [1f0, 2f0], y = SA[4f0, 5f0]);  # partly mutable model

julia> t = Optimisers.setup(Momentum(1/30, 0.9), m)  # tree of states
(x = Leaf(Momentum(0.0333333, 0.9), Float32[0.0, 0.0]), y = Leaf(Momentum(0.0333333, 0.9), Float32[0.0, 0.0]))

julia> g = gradient(m -> sum(abs2.(m.x .+ m.y)), m)[1]  # structural gradient
(x = Float32[10.0, 14.0], y = Float32[10.0, 14.0])

julia> t2, m2 = Optimisers.update!(t, m, g);

julia> m2  # after update or update!, this is the new model
(x = Float32[0.6666666, 1.5333333], y = Float32[3.6666667, 4.5333333])

julia> m2.x === m.x  # update! has re-used this array, for efficiency
true

julia> m  # original should be discarded, may be mutated but no guarantee
(x = Float32[0.6666666, 1.5333333], y = Float32[4.0, 5.0])

julia> t == t2  # original state tree is guaranteed to be mutated
true
```
