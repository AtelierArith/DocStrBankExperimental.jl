```
AbstractManifoldGradientObjective{E<:AbstractEvaluationType, TC, TG} <: AbstractManifoldCostObjective{E, TC}
```

勾配を提供するすべての目的のための抽象型であり、ここで `T` は勾配関数のための [`AbstractEvaluationType`](@ref) です。
