```
OptimisersOptimizer(opt; maxeval = 10^5, maxtime = Inf, min_grad_norm = 1e-8, lower_bounds = -Inf, upper_bounds = Inf)
```

Optimizer `opt` can be anything from `subtypes(Optimisers.AbstractRule)`. Optimization stops, when the L2-norm of the gradient falls below `min_grad_norm` or `maxeval` or `maxtime` is reached. See also [Optimisers](https://fluxml.ai/Optimisers.jl/dev/api/).
