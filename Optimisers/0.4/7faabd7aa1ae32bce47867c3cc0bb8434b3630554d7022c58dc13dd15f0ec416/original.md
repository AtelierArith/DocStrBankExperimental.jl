```
Optimisers.freeze!(tree)
```

Temporarily alters the state `tree = setup(rule, model)` so that parameters will not be updated. Un-done by [`thaw!`](@ref Optimisers.thaw!).

Can be applied to the state corresponding to only part of a model, for instance with `model::Chain`, to freeze `model.layers[1]` you should call `freeze!(tree.layers[1])`.

# Example

```jldoctest
julia> m = (x = ([1.0], 2.0), y = [3.0]);

julia> s = Optimisers.setup(Momentum(), m);

julia> Optimisers.freeze!(s.x)

julia> Optimisers.update!(s, m, (x = ([pi], 10pi), y = [100pi]));  # with fake gradient

julia> m
(x = ([1.0], 2.0), y = [-0.14159265358979312])

julia> s
(x = (Leaf(Momentum(0.01, 0.9), [0.0], frozen = true), ()), y = Leaf(Momentum(0.01, 0.9), [3.14159]))

julia> Optimisers.thaw!(s)

julia> s.x
(Leaf(Momentum(0.01, 0.9), [0.0]), ())
```
