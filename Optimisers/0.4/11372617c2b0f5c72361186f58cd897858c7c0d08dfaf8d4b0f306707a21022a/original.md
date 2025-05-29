```
Optimisers.setup(rule, model) -> state_tree
```

Initialises the given optimiser for every trainable parameter within the model. Returns a tree of the relevant states, which must be passed to [`update`](@ref Optimisers.update) or [`update!`](@ref Optimisers.update!).

# Example

```jldoctest
julia> m = (x = rand(3), y = (true, false), z = tanh);

julia> Optimisers.setup(Momentum(), m)  # same field names as m
(x = Leaf(Momentum(0.01, 0.9), [0.0, 0.0, 0.0]), y = ((), ()), z = ())
```

The recursion into structures uses Functors.jl, and any new `struct`s containing parameters need to be marked with `Functors.@functor` before use. See [the Flux docs](https://fluxml.ai/Flux.jl/stable/models/advanced/) for more about this.

```jldoctest
julia> struct Layer; mat; fun; end

julia> model = (lay = Layer([1 2; 3 4f0], sin), vec = [5, 6f0]);

julia> Optimisers.setup(Momentum(), model)  # new struct is by default ignored
(lay = (), vec = Leaf(Momentum(0.01, 0.9), Float32[0.0, 0.0]))

julia> destructure(model)
(Float32[5.0, 6.0], Restructure(NamedTuple, ..., 2))

julia> using Functors; @functor Layer  # annotate this type as containing parameters

julia> Optimisers.setup(Momentum(), model)
(lay = (mat = Leaf(Momentum(0.01, 0.9), Float32[0.0 0.0; 0.0 0.0]), fun = ()), vec = Leaf(Momentum(0.01, 0.9), Float32[0.0, 0.0]))

julia> destructure(model)
(Float32[1.0, 3.0, 2.0, 4.0, 5.0, 6.0], Restructure(NamedTuple, ..., 6))
```
