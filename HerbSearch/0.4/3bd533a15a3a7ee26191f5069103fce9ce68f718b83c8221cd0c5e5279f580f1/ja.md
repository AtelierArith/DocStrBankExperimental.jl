```
GeneticSearchIterator{FitnessFunction,CrossOverFunction,MutationFunction,SelectParentsFunction,EvaluationFunction} <: ProgramIterator
```

遺伝的探索を使用して[`ProgramIterator`](@ref)を定義します。

構成要素は次のとおりです：

  * `examples::Vector{<:IOExample}`: 仕様を定義する例のコレクション
  * `evaluation_function::EvaluationFunction`: 個々のプログラムを評価するためのインタープリタ
  * `population_size::Int64`: 集団内の個体数
  * `mutation_probability::Float64`: 各個体の突然変異の確率
  * `maximum_initial_population_depth::Int64`: 集団が初期化されるときの木の最大深さ

end
