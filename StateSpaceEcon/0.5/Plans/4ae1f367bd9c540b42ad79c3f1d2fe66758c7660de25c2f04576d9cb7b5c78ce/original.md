```
Plan(model, range)
```

Create a default simulation plan for the given model over the given range. The range of the plan is augmented to include periods before and after the given range, over which initial and final conditions will be applied.

Instead of a range, one could also pass in a single moment in time ([`MIT`](@ref TimeSeriesEcon.MIT)) instance, in which case it is interpreted as a range of length 1.
