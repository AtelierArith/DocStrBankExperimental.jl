```
SingleHeadedBranch(covariate_idx, neurons; activation, init_bias).
```

Luxモデルでブランチを作成するための便利な関数です。指定された数の`neurons`を持つ単一の隠れ層ニューラルネットワークを構築します。解釈を容易にするために、モデルへの入力としては最大で2つの共変量を使用することをお勧めします。

# 引数:

  * `covariate_idx::Union{AbstractVector{<:Int}, Int}`: ブランチで使用する共変量のインデックス。
  * `neurons::Int`: 隠れ層のニューロンの数。
  * `activation`: 隠れ層で使用する活性化関数。デフォルト = swish。
  * `init_bias`: バイアスパラメータの初期化関数。デフォルト = ones32。初期推定を改善するのに役立ちます。
