```
get_gradient(M::AbstractManifold, sgo::ManifoldStochasticGradientObjective, p, k)
get_gradient!(M::AbstractManifold, sgo::ManifoldStochasticGradientObjective, Y, p, k)
```

Evaluate one of the summands gradients $\operatorname{grad}f_k$, $k∈\{1,…,n\}$, at `x` (in place of `Y`).

If you use a single function for the stochastic gradient, that works in-place, then `get_gradient` is not available, since the length (or number of elements of the gradient required for allocation) can not be determined.
