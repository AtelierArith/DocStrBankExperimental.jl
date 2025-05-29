```julia
manifoldProduct(ff; ...)
manifoldProduct(
    ff,
    mani;
    makeCopy,
    Niter,
    ndims,
    N,
    u0,
    oldPoints,
    addEntropy,
    recordLabels,
    selectedLabels,
    _randU,
    _randN,
    logger,
    bws
)

```

Approximate the pointwise the product of functionals on manifolds using KernelDensityEstimate.

Notes:

  * Always pass full beliefs, for partials use for e.g. `partialDimsWorkaround=[1;3;6]`
  * Can also multiply different partials together

## Example

```julia
# setup
M = TranslationGroup(3)
N = 75
p = manikde!(M, [randn(3) for _ in 1:N])
q = manikde!(M, [randn(3) .+ 1 for _ in 1:N])

# approximate the product between hybrid manifold densities
pq = manifoldProduct([p;q])

# direct histogram plot
using Gadfly
plot( x=getPoints(pq)[1,:], y=getPoints(pq)[2,:], Geom.histogram2d )

# TODO, convenient plotting (work in progress...)
```
