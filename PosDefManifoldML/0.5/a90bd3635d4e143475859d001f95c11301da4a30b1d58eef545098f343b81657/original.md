```julia
function dim(pipeline::Pipeline)
```

Return the dimension determined by a fitted [`Recenter`](@ref) pre-conditioner  if the `pipeline` comprises such a pre-conditioner, `nothing` otherwise.  This is used to adapt pipelines - see the documentation of the [`fit!`](@ref) function for ENLR machine learning models for an example.

**Examples**

```julia
using PosDefManifoldML, PosDefManifold

pipeline = @→ Recenter(; eVar=0.9) → Shrink()
dim(pipeline) # return false, as it is not fitted

P = randP(10, 5)
p = fit!(P, pipeline)
dim(p) # return an integer ≤ 10
```

**Learn the package**: check out [`@pipeline`](@ref)
