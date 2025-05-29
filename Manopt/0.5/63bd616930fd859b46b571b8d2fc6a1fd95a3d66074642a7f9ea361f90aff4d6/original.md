```
AbstractManoptSolverState
```

A general super type for all solver states.

# Fields

The following fields are assumed to be default. If you use different ones, adapt the the access functions [`get_iterate`](@ref) and [`get_stopping_criterion`](@ref) accordingly

  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
