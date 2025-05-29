```
viterbi(model::HiddenMarkovModel, Y::Matrix{<:Real}, X::Union{Matrix{<:Real},Nothing}=nothing;)
```

Viterbiアルゴリズムを使用して最も可能性の高いクラスラベルを取得します

# 引数

  * `model::HiddenMarkovModel`: 適合させる隠れマルコフモデル。
  * `Y::Matrix{<:Real}`: 放出データ
  * `X::Union{Matrix{<:Real},Nothing}=nothing`: スイッチング回帰モデルの適合のためのオプションの入力データ

# 戻り値

  * `best_path::Vector{Float64}`: 各時点での最も可能性の高い状態ラベル
