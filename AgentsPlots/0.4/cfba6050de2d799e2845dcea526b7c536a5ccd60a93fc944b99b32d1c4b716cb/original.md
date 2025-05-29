```
plotabm(model::ABM{<: ContinuousSpace}; ac, as, am, kwargs...)
plotabm(model::ABM{<: DiscreteSpace}; ac, as, am, kwargs...)
```

Plot the `model` as a `scatter`-plot, by configuring the agent shape, color and size via the keywords `ac, as, am`. These keywords can be constants, or they can be functions, each accepting an agent and outputting a valid value for color/shape/size.

The keyword `scheduler = model.scheduler` decides the plotting order of agents (which matters only if there is overlap).

The keyword `offset` is a function with argument `offest(a::Agent)`. It targets scenarios where multiple agents existin within a grid cell as it adds an offset (same type as `agent.pos`) to the plotted agent position.

All other keywords are propagated into `Plots.scatter` and the plot is returned.
