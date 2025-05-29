```
Optimisers.adjust!(tree, η)
```

Alters the state `tree = setup(rule, model)` to change the parameters of the optimisation rule, without destroying its stored state. Typically used mid-way through training.

Can be applied to part of a model, by acting only on the corresponding part of the state `tree`.

To change just the learning rate, provide a number `η::Real`.

# Example

```jldoctest adjust
julia> m = (vec = rand(Float32, 2), fun = sin);

julia> st = Optimisers.setup(Nesterov(), m)  # stored momentum is initialised to zero
(vec = Leaf(Nesterov(0.001, 0.9), Float32[0.0, 0.0]), fun = ())

julia> st, m = Optimisers.update(st, m, (vec = [16, 88], fun = nothing));  # with fake gradient

julia> st
(vec = Leaf(Nesterov(0.001, 0.9), Float32[-0.016, -0.088]), fun = ())

julia> Optimisers.adjust!(st, 0.123)  # change learning rate, stored momentum untouched

julia> st
(vec = Leaf(Nesterov(0.123, 0.9), Float32[-0.016, -0.088]), fun = ())
```

To change other parameters, `adjust!` also accepts keyword arguments matching the field names of the optimisation rule's type.

```jldoctest adjust
julia> fieldnames(Adam)
(:eta, :beta, :epsilon)

julia> st2 = Optimisers.setup(OptimiserChain(ClipGrad(), Adam()), m)
(vec = Leaf(OptimiserChain(ClipGrad(10.0), Adam(0.001, (0.9, 0.999), 1.0e-8)), (nothing, (Float32[0.0, 0.0], Float32[0.0, 0.0], (0.9, 0.999)))), fun = ())

julia> Optimisers.adjust(st2; beta = (0.777, 0.909), delta = 11.1)  # delta acts on ClipGrad
(vec = Leaf(OptimiserChain(ClipGrad(11.1), Adam(0.001, (0.777, 0.909), 1.0e-8)), (nothing, (Float32[0.0, 0.0], Float32[0.0, 0.0], (0.9, 0.999)))), fun = ())

julia> Optimisers.adjust(st; beta = "no such field")  # silently ignored!
(vec = Leaf(Nesterov(0.123, 0.9), Float32[-0.016, -0.088]), fun = ())
```
