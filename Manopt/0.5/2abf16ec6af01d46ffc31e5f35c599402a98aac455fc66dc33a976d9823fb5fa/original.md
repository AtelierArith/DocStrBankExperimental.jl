```
get_gradient(M::AbstractManifold, sgo::ManifoldStochasticGradientObjective, p)
get_gradient!(M::AbstractManifold, sgo::ManifoldStochasticGradientObjective, X, p)
```

Evaluate the complete gradient $\operatorname{grad} f = \displaystyle\sum_{i=1}^n \operatorname{grad} f_i(p)$ at `p` (in place of `X`).

If you use a single function for the stochastic gradient, that works in-place, then [`get_gradient`](@ref) is not available, since the length (or number of elements of the gradient required for allocation) can not be determined.
