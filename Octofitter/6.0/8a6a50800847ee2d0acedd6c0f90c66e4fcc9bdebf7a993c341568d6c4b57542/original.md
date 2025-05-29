```
@system [system_name] begin
    [prior_1] ~ [UnivariateDistribution]
    [prior_2] ~ [UnivariateDistribution]
    calculation_3 = system.[prior_1] + system.[prior_2]
end [likelihood_objects...] [planet_models...]
```

Generate a System model named `system_name`. A variable will be created with the name `[system_name]` in the current scope. Following that is a block of variable assignments. Variables with a `~` will be free variables with a prior distribution given by the right-hand-side (a UnivariateDistribution from Distributions.jl or a `KDEDist`).  Calculated quantities are also allowed. These may reference other variables using the planet name followed by a dot and the name of the variable. Variables from other planets in a single system are not accessible. You can access other variables in the current local scope, but these bindings are only guaranteed to be resolved a single time. Note that using non-constant global variables in calculated expressions can lead  to poor performance. After the end of the variable block, the system model can be conditioned on data by supplying zero or more likelihood objects. Finally, zero or more planet models can be attached to the system, potentially conditioned on likelihood objects of their own.
