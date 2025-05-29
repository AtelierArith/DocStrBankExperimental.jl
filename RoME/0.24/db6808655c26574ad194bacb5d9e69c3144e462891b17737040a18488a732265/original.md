```julia
struct DynPose2 <: DistributedFactorGraphs.InferenceVariable
```

Dynamic pose variable with velocity components: `x, y, theta, dx/dt, dy/dt`

Note

  * The `SE2E2_Manifold` definition used currently is a hack to simplify the transition to Manifolds.jl, see #244
  * Replaced `SE2E2_Manifold` hack with `ProductManifold(SpecialEuclidean(2), TranslationGroup(2))`, confirm if it is correct.
