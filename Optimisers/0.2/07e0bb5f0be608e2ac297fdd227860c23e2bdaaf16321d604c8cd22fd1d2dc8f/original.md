```
OptimiserChain(opts...)
```

Compose a sequence of optimisers so that each `opt` in `opts` updates the gradient, in the order specified.

With an empty sequence, `OptimiserChain()` is the identity, so `update!` will subtract the full gradient from the parameters. This is equivalent to `Descent(1)`.

# Example

```jldoctest
julia> o = OptimiserChain(ClipGrad(1.0), Descent(0.1));

julia> m = (zeros(3),);

julia> s = Optimisers.setup(o, m)
(Leaf(OptimiserChain(ClipGrad{Float64}(1.0), Descent{Float64}(0.1)), (nothing, nothing)),)

julia> Optimisers.update(s, m, ([0.3, 1, 7],))[2]  # clips before discounting
([-0.03, -0.1, -0.1],)
```
