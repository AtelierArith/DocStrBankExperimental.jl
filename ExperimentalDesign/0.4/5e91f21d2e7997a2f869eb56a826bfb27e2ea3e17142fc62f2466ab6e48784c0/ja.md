```julia
struct OptimalDesign <: ExperimentalDesign.AbstractOptimalDesign
```

  * `matrix::DataFrames.DataFrame`
  * `factors::NamedTuple`
  * `formula::StatsModels.FormulaTerm`
  * `selected_experiments::Array{Int64}`
  * `criteria::Dict{Symbol, Float64}`

候補実験のセット、目標最適性基準、およびモデル事前式を含みます。与えられた最適性基準を最大化する実験のセットは、候補セットから[`kl_exchange`](@ref)アルゴリズムを使用して選択できます。
