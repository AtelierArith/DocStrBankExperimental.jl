getAggHamSystemBath(agg, aggTools.indices,  	franckCondonFactors; groundEnergy = false) getAggHamSystemBath(agg, aggTools.indices; groundEnergy = false) getAggHamSystemBath(agg; groundEnergy = false)

[`Aggregate`](@ref) のシステムとバスのハミルトニアンを DenseOperator の形式で取得します。

# 引数

  * `agg`: [`Aggregate`](@ref) のインスタンス。
  * `aggTools.indices`: [`getIndices`](@ref) によって生成されたアグリゲートインデックス。
  * `franckCondonFactors`: [`getFranckCondonFactors`](@ref) によって生成されたフランク・コンダン因子。
