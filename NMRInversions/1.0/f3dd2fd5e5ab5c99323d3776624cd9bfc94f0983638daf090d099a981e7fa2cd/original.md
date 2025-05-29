```
lcurve(start; kwargs...)
```

Constructor for finding the optimal alpha value via lcurve curvature box optimization, given a starting value.

Necessary (positional) arguments:

  * `start` is the starting alpha value.

Choose something sensible, usually a value between 0.1 and 10 would work well.

Optional (keyword) arguments:

  * `algorithm` determines which method will be used by Optim.jl to solve the problem.

Default is LBFGS(). Only first order optimizers can be chosen here.  For more details, refer to Optim.jl documentation.

  * `opts` an Optim.Options() structure which can provide some preferences to the solver.

Please have a look [here](https://julianlsolvers.github.io/Optim.jl/v1.10/user/config/).
