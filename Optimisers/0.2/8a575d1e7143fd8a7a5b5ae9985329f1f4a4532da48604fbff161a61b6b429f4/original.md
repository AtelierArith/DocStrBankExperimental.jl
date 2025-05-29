```
AccumGrad(n::Int)
```

A rule constructed `OptimiserChain(AccumGrad(n), Rule())` will accumulate for `n` steps, before applying `Rule` to the mean of these `n` gradients.

This is useful for training with effective batch sizes too large for the available memory. Instead of computing the gradient for batch size `b` at once, compute it for size `b/n` and accumulate `n` such gradients.

# Example

```jldoctest
julia> m = (x=[1f0], y=[2f0]);

julia> r = OptimiserChain(AccumGrad(2), WeightDecay(0.01), Descent(0.1));

julia> s = Optimisers.setup(r, m);

julia> Optimisers.update!(s, m, (x=[33], y=[0]));

julia> m  # model not yet changed
(x = Float32[1.0], y = Float32[2.0])

julia> Optimisers.update!(s, m, (x=[0], y=[444]));

julia> m  # n=2 gradients applied at once
(x = Float32[-0.651], y = Float32[-20.202])
```
