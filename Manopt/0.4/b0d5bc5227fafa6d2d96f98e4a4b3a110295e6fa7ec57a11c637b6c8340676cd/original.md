```
ManifoldDifferenceOfConvexProximalObjective{E} <: Problem
```

Specify an objective [`difference_of_convex_proximal_point`](@ref) algorithm. The problem is of the form

$$
    \operatorname*{argmin}_{p∈\mathcal M} g(p) - h(p)
$$

where both $g$ and $h$ are convex, lower semicontinuous and proper.

# Fields

  * `cost`:     (`nothing`) implementation of $f(p) = g(p)-h(p)$ (optional)
  * `gradient`: the gradient of the cost
  * `grad_h!!`: a function $\operatorname{grad}h: \mathcal M → T\mathcal M$,

Note that both the gradients might be given in two possible signatures as allocating or in-place.

# Constructor

```
ManifoldDifferenceOfConvexProximalObjective(gradh; cost=nothing, gradient=nothing)
```

an note that neither cost nor gradient are required for the algorithm, just for eventual debug or stopping criteria.
