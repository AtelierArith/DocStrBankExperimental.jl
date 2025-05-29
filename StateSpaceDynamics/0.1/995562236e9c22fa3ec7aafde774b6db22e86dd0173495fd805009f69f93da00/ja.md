```
function class_probabilities(model::HiddenMarkovModel, Y::Matrix{<:Real}, X::Union{Matrix{<:Real},Nothing}=nothing;)
```

フォワード・バックワードアルゴリズムを使用して各時間点でのクラス確率を計算します

# 引数

  * `model::HiddenMarkovModel`: フィッティングする隠れマルコフモデル。
  * `Y::Matrix{<:Real}`: 放出データ
  * `X::Union{Matrix{<:Real},Nothing}=nothing`: スイッチング回帰モデルのフィッティングのためのオプションの入力データ

# 戻り値

  * `class_probabilities::Matrix{Float64}`: 各時間点でのクラス確率
