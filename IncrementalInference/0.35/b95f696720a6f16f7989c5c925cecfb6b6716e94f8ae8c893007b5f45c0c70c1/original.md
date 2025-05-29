```julia
struct CommonConvWrapper{T<:DistributedFactorGraphs.AbstractFactor, VT<:Tuple, TP<:(Base.RefValue{<:Tuple}), CT, AM<:ManifoldsBase.AbstractManifold, HR<:IncrementalInference.HypoRecipeCompute, MT, G} <: DistributedFactorGraphs.FactorOperationalMemory
```

Main factor memory container used during inference operations – i.e. values specific to one complete convolution operation

Notes

  * CCW does not get serialized / persisted
  * At writing, the assumption is there is just one CCW per factor
  * Any multithreaded design needs to happens as sub-constainers inside CCW or otherwise, to carry separate memory.
  * Since #467, `CalcFactor` is the only type 'seen by user' during `getSample` or function residual calculations `(cf::CalcFactor{<:MyFactor})`, s.t. `MyFactor <: AbstractRelative___`
  * There also exists a `CalcFactorMahalanobis` for parameteric computations using as much of the same mechanics as possible.
  * CCW is consolidated object of other previous types, FMD CPT CF CFM.

Related 

[`CalcFactor`](@ref), [`CalcFactorMahalanobis`](@ref)
