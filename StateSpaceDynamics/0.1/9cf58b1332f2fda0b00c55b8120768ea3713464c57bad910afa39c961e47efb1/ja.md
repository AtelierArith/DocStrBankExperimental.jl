```
function class_probabilities(model::HiddenMarkovModel, Y::Vector{<:Matrix{<:Real}}, X::Union{Vector{<:Matrix{<:Real}},Nothing}=nothing;)
```

複数のデータ試行に対して前向き後ろ向きアルゴリズムを使用して各時間点でのクラス確率を計算します

# 引数

  * `model::HiddenMarkovModel`: フィッティングする隠れマルコフモデル。
  * `Y::Vectpr{<:Matrix{<:Real}}`: 発生データの試行
  * `X::Union{Vector{<:Matrix{<:Real}},Nothing}=nothing`: スイッチング回帰モデルのフィッティングのためのオプションの入力データの試行

# 戻り値

  * `class_probabilities::Vector{<:Matrix{Float64}}`: 各試行の各時間点でのクラス確率

```
