```
sample(model::HiddenMarkovModel, data...; n::Int)
```

隠れマルコフモデルから `n` サンプルを生成します。状態列と観測列のタプルを返します。

# 引数

  * `model::HiddenMarkovModel`: サンプリングする隠れマルコフモデル。
  * `data...`: 隠れマルコフモデルにフィットさせるデータ。発生モデルと同じ形式が必要です。
  * `n::Int`: 生成するサンプルの数。

# 返り値

  * `state_sequence::Vector{Int}`: 状態列で、各要素は整数 1:K です。
  * `observation_sequence::Matrix{Float64}`: 観測列。この形式は発生モデルの出力に従います。
