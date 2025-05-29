```
viterbi(model::HiddenMarkovModel, Y::Vector{<:Matrix{<:Real}}, X::Union{Vector{<:Matrix{<:Real}},Nothing}=nothing;)
```

Viterbiアルゴリズムを使用して、複数のデータ試行の最も可能性の高いクラスラベルを取得します。

# 引数

  * `model::HiddenMarkovModel`: 適合させる隠れマルコフモデル。
  * `Y::Vectpr{<:Matrix{<:Real}}`: 放出データの試行
  * `X::Union{Vector{<:Matrix{<:Real}},Nothing}=nothing`: スイッチング回帰モデルの適合のためのオプションの入力データの試行

# 戻り値

  * `best_path::Vector{<:Vector{Float64}}`: 各試行の最良の状態パス
