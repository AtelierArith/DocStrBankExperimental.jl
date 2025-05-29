```
plotabm(model::ABM{<: GraphSpace}; ac, as, am, kwargs...)
```

This function is the same as `plotabm` for `ContinuousSpace`, but here the three key functions `ac, as, am` do not get an agent as an input but a vector of agents at each node of the graph. Their output is the same.

Here `as` defaults to `length`. Internally, the `graphplot` recipe is used, and all other `kwargs...` are propagated there.
