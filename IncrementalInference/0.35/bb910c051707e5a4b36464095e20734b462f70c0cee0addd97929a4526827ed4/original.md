```julia
struct LinearRelative{N, T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

Default linear offset between two scalar variables.

$$
X_2 = X_1 + η_Z
$$
