```julia
initVariable!(
    variable::DistributedFactorGraphs.VariableCompute,
    ptsArr::ApproxManifoldProducts.ManifoldKernelDensity;
    ...
)
initVariable!(
    variable::DistributedFactorGraphs.VariableCompute,
    ptsArr::ApproxManifoldProducts.ManifoldKernelDensity,
    solveKey::Symbol;
    dontmargin,
    N
)

```

Method to manually initialize a variable using a set of points.

Notes

  * Disable automated graphinit on `addFactor!(fg, ...; graphinit=false)

      * any un-initialized variables will automatically be initialized by `solveTree!`

Example:

```julia
# some variable is added to fg
addVariable!(fg, :somepoint3, ContinuousEuclid{2})

# data is organized as (row,col) == (dimension, samples)
pts = randn(2,100)
initVariable!(fg, :somepoint3, pts)

# manifold management should be done automatically.
# note upgrades are coming to consolidate with Manifolds.jl, see RoME #244

## it is also possible to initVariable! by using existing factors, e.g.
initVariable!(fg, :x3, [:x2x3f1])
```

DevNotes

  * TODO better document graphinit and treeinit.
