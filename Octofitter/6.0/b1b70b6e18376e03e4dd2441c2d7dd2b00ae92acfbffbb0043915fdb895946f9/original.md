```
@planet [planet_name] [Orbit_Type] begin
    [prior_1] ~ [UnivariateDistribution]
    [prior_2] ~ [UnivariateDistribution]
    calculation_3 = [planet_name].[prior_1] + [planet_name].[prior_2] + [system.variable_x]
end [likelihood_objects...]
```

Generate a Planet model named `planet_name`. A variable will be created with the name `[planet_name]` in the current scope. `Orbit_Type` specifies the orbit parameterization from PlanetOrbits.jl. You must provide all input variables needed for the selected orbit type (see PlanetOrbits.jl documentation). Following that is a block of variable assignments. Variables with a `~` will be free variables with a prior distribution given by the right-hand-side (a UnivariateDistribution from Distributions.jl or a `KDEDist`).  Calculated quantities are also allowed. These may reference other variables using the planet name followed by a dot and the name of the variable. Variables from other planets in a single system are not accessible. You can access other variables in the current local scope, but these bindings are only guaranteed to be resolved a single time. Note that using non-constant global variables in calculated expressions can lead  to poor performance. Finally, the planet model can be conditioned on data by supplying zero or more likelihood objects.
