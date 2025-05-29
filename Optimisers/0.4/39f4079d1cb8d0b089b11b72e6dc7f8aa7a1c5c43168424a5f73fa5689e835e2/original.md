```
Optimisers.update(tree, model, gradient) -> (tree, model)
```

Uses the optimiser and the gradient to change the trainable parameters in the model. Returns the improved model, and the optimiser states needed for the next update. The initial tree of states comes from [`setup`](@ref Optimisers.setup).

See also [`update!`](@ref Optimisers.update!), which will be faster for models of ordinary `Array`s or `CuArray`s.

# Example

```jldoctest
julia> m = (x = Float32[1,2,3], y = tanh);

julia> t = Optimisers.setup(Descent(0.1), m)
(x = Leaf(Descent(0.1), nothing), y = ())

julia> g = (x = [1,1,1], y = nothing);  # fake gradient

julia> Optimisers.update(t, m, g)
((x = Leaf(Descent(0.1), nothing), y = ()), (x = Float32[0.9, 1.9, 2.9], y = tanh))
```
