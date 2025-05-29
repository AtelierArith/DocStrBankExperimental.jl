```
get_gradients(M::AbstractManifold, sgo::ManifoldStochasticGradientObjective, p)
get_gradients!(M::AbstractManifold, X, sgo::ManifoldStochasticGradientObjective, p)
```

Evaluate all summands gradients $\{\operatorname{grad}f_i\}_{i=1}^n$ at `p` (in place of `X`).

If you use a single function for the stochastic gradient, that works in-place, then [`get_gradient`](@ref) is not available, since the length (or number of elements of the gradient) can not be determined.
