```
sample(model::AutoRegressionEmission, Y_prev::Matrix{<:Real}; observation_sequence::Matrix{<:Real}=Matrix{Float64}(undef, 0, model.output_dim))
```

与えられた自己回帰エミッションモデルからサンプルを生成し、前の観測 `Y_prev` を使用して、提供された観測シーケンスに追加します。

# 引数

  * `model::AutoRegressionEmission`: サンプリングする自己回帰エミッションモデル。
  * `Y_prev::Matrix{<:Real}`: 各行が観測を表す前の観測の行列。
  * `observation_sequence::Matrix{<:Real}`: 新しいサンプルが追加される観測のシーケンス（適切な次元の空の行列がデフォルト）。

# 戻り値

  * `Matrix{Float64}`: 新しいサンプルが追加された更新された観測シーケンス。
