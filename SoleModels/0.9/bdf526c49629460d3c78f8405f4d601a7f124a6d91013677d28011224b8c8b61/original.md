```
abstract type AbstractModel{O} end
```

Abstract type for symbolic models that, given an instance object (i.e., a piece of data), output an outcome of type `O`.

A model is said to be *symbolic* when its application relies on checking formulas of a certain logical language (see [SoleLogics.jl](https://github.com/aclai-lab/SoleLogics.jl) package) on the instance. Symbolic models provide a form of transparent and *interpretable modeling*, as a symbolic model can be synthethised into a set of mutually exclusive logical rules that can often be translated into natural language.

Examples of symbolic models are [`Rule`](@ref)s, [`Branch`](@ref)es, [`DecisionList`](@ref)s and [`DecisionTree`](@ref)s. Examples of non-symbolic (or *sub-symbolic*) models include those encoding algebraic mathematical functions (e.g., neural networks).

Symbolic models can wrap other `AbstractModel`s, and use them to compute the outcome. As such, an `AbstractModel` can actually be the result of a composition of many models, and enclose a *tree* of `AbstractModel`s (with `LeafModel`s at the leaves).

# TODO - bring missing dispatches here (do the same for other model types)

# Interface

  * `apply(m::AbstractModel, i::AbstractInterpretation; kwargs...)`
  * `iscomplete(m::AbstractModel)`
  * `outcometype(m::AbstractModel)`
  * `outputtype(m::AbstractModel)`
  * `immediatesubmodels(m::AbstractModel)`
  * `nimmediatesubmodels(m::AbstractModel)`
  * `leafmodels(m::AbstractModel)`
  * `nleafmodels(m::AbstractModel)`
  * `listimmediaterules(m::AbstractModel)`
  * `info(m::AbstractModel, [key, [defaultval]])`
  * `info!(m::AbstractModel, key, value)`
  * `hasinfo(m::AbstractModel, key)`
  * `listrules(m::AbstractModel; kwargs...)`

# Utility functions

  * `apply(m::AbstractModel, i::AbstractInterpretationSet; kwargs...)`
  * See AbstractTrees...

# Utility functions

  * `apply(m::AbstractModel, d::AbstractInterpretationSet, i_instance::Integer; kwargs...)
  * `submodels(m::AbstractModel)`(fallback of the general   `AbstractTrees.children(m::AbstractModel)`)
  * `nsubmodels(m::AbstractModel)`
  * `subtreeheight(m::AbstractModel)`
  * `listrules(       m::AbstractModel;       use_shortforms::Bool=true,       use_leftmostlinearform::Union{Nothing,Bool}=nothing,       normalize::Bool=false,       force_syntaxtree::Bool=false,   )`
  * `joinrules(m::AbstractModel, silent=false; kwargs...)`

# Examples

TODO

See also [`apply`](@ref), [`Branch`](@ref), [`info`](@ref), [`iscomplete`](@ref), [`LeafModel`](@ref), [`outcometype`](@ref), [`Rule`](@ref).
