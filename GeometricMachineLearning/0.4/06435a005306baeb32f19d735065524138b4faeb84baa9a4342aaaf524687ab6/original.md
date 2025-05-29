```
AdamCache(Y)
```

Store the first and second moment for `Y` (initialized as zeros).

First and second moments are called `B₁` and `B₂`.

If the cache is called with an instance of a homogeneous space, e.g. the [`StiefelManifold`](@ref) $St(n,N)$ it initializes the moments as elements of $\mathfrak{g}^\mathrm{hor}$ ([`StiefelLieAlgHorMatrix`](@ref)).

# Examples

```jldoctest
using GeometricMachineLearning

Y = rand(StiefelManifold, 5, 3)
AdamCache(Y).B₁

# output

5×5 StiefelLieAlgHorMatrix{Float64, SkewSymMatrix{Float64, Vector{Float64}}, Matrix{Float64}}:
 0.0  -0.0  -0.0  -0.0  -0.0
 0.0   0.0  -0.0  -0.0  -0.0
 0.0   0.0   0.0  -0.0  -0.0
 0.0   0.0   0.0   0.0   0.0
 0.0   0.0   0.0   0.0   0.0
```
