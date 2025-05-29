```julia
mutable struct PriorCircular{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractPrior
```

すべての次元の円形変数に対する直接観測を導入します：

## 例：

```julia
PriorCircular( MvNormal([10; 10; pi/6.0], diagm([0.1;0.1;0.05].^2)) )
```

関連

[`Circular`](@ref), [`Prior`](@ref), [`PartialPrior`](@ref)
