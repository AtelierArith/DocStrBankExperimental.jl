```julia
struct PriorVelPos3{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractPrior
```

すべての次元のPose2変数に対する直接観測を導入します：

## 例：

```julia
PriorVelPos3( MvNormal(zeros(6), Matrix(Diagonal(ones(6).^2))) )
```
