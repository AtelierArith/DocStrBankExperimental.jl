```
step!(sd::AbstractSimData)
```

Allows stepping a simulation one frame at a time, for a more manual approach to simulation that `sim!`. This may be useful if other processes need to be run  between steps, or the simulation is of variable length. `step!` also removes the use of `Output`s, meaning storing of grid data must be handled manually, if that is  required. Of course, an output can also be updated manually, using:

```julia
DynmicGrids.storeframe!(output, simdata)
```

Instead of an `Output`, the internal [`SimData`](@ref) objects are used directly,  and can be defined using a [`Extent`](@ref) object and a [`Ruleset`](@ref).

# Example

```julia
using DynmicGrids, Plots
ruleset = Ruleset(Life(); proc=ThreadedCPU())
extent = Extent(; init=(a=A, b=B), aux=aux, tspan=tspan)
simdata = SimData(extent, ruleset)

# Run a single step, which returns an updated `SimData` object
simdata = step!(simdata)
# Get a view of the grid without padding
grid = DynmicGrids.gridview(simdata[:a])
heatmap(grid)
```

This example returns a `GridData` object for the `:a` grid, which is `<: AbstractAray`.
