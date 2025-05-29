```julia
mutable struct LikelihoodMessage{T<:IncrementalInference.MessageType} <: DistributedFactorGraphs.AbstractPrior
```

木構造上でのメッセージパッシングのための信念メッセージ。これは不完全な結合確率と見なされるべきです。

ノート:

  * belief -> [`TreeBelief`](@ref) の辞書
  * variableOrder -> cliqueLikelihood のセパレータの順序付き変数IDリスト
  * cliqueLikelihood -> クリークセパレータに関する周辺分布 (<: `SamplableBelief`)。
  * 古い名前には、productFactor、Fnew、MsgPrior、LikelihoodMessage が含まれます。

開発ノート:

  * 非パラメトリックとパラメトリックの両方で使用されます。
  * パラメトリックケースの目的: `MvNormal(μ=[:x0;:x2;:l5], Σ=[+ * *; * + *; * * +])`。
  * 統合努力の一部、#459 を参照。
  * デコンボリューションを使用して、結合構造のためのより良い条件付けが進行中、#579、#635 を参照。

      * TODO <: Singleton の理由を確認する。
  * `sender::@NamedTuple{id::Int64, step::Int64}`
  * `status::IncrementalInference.CliqStatus`
  * `belief::Dict{Symbol, IncrementalInference.TreeBelief}`
  * `variableOrder::Vector{Symbol}`
  * `cliqueLikelihood::Union{Nothing, IncrementalInference.AliasingScalarSampler, KernelDensityEstimate.BallTreeDensity, Distributions.Distribution, IncrementalInference.FluxModelsDistribution, IncrementalInference.HeatmapGridDensity, IncrementalInference.LevelSetGridNormal, ApproxManifoldProducts.MKD{M, B} where {M<:ManifoldsBase.AbstractManifold, B<:(Union{var"#s20", var"#s19"} where {var"#s20"<:ApproxManifoldProducts.ManellicTree, var"#s19"<:KernelDensityEstimate.BallTreeDensity})}}`
  * `msgType::IncrementalInference.MessageType`
  * `hasPriors::Bool`
  * `childSolvDims::Dict{Int64, Float64}`
  * `jointmsg::IncrementalInference._MsgJointLikelihood`

```
