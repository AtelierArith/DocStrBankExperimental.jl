```julia
mutable struct LikelihoodMessage{T<:IncrementalInference.MessageType} <: DistributedFactorGraphs.AbstractPrior
```

Belief message for message passing on the tree.  This should be considered an incomplete joint probility.

Notes:

  * belief -> Dictionary of [`TreeBelief`](@ref)
  * variableOrder -> Ordered variable id list of the seperators in cliqueLikelihood
  * cliqueLikelihood -> marginal distribution (<: `SamplableBelief`) over clique seperators.
  * Older names include: productFactor, Fnew, MsgPrior, LikelihoodMessage

DevNotes:

  * Used by both nonparametric and parametric.
  * Objective for parametric case: `MvNormal(μ=[:x0;:x2;:l5], Σ=[+ * *; * + *; * * +])`.
  * Part of the consolidation effort, see #459.
  * Better conditioning for joint structure in the works using deconvolution, see #579, #635.

      * TODO confirm why <: Singleton.

  * `sender::@NamedTuple{id::Int64, step::Int64}`
  * `status::IncrementalInference.CliqStatus`
  * `belief::Dict{Symbol, IncrementalInference.TreeBelief}`
  * `variableOrder::Vector{Symbol}`
  * `cliqueLikelihood::Union{Nothing, IncrementalInference.AliasingScalarSampler, KernelDensityEstimate.BallTreeDensity, Distributions.Distribution, IncrementalInference.FluxModelsDistribution, IncrementalInference.HeatmapGridDensity, IncrementalInference.LevelSetGridNormal, ApproxManifoldProducts.MKD{M, B} where {M<:ManifoldsBase.AbstractManifold, B<:(Union{var"#s20", var"#s19"} where {var"#s20"<:ApproxManifoldProducts.ManellicTree, var"#s19"<:KernelDensityEstimate.BallTreeDensity})}}`
  * `msgType::IncrementalInference.MessageType`
  * `hasPriors::Bool`
  * `childSolvDims::Dict{Int64, Float64}`
  * `jointmsg::IncrementalInference._MsgJointLikelihood`
