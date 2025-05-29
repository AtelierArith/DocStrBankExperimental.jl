```
MultiHeadedBranch(covariate_idx, neurons, heads; activation, init_bias).
```

Luxモデルでブランチを作成するための便利な関数です。`heads`で指定された複数の独立した層に並行して接続される単一の隠れ層を含むニューラルネットワークを構築します。この方法により、共変量効果は類似のベースを共有しますが、各ヘッドのために独立した効果を学習することができます。すべての隠れ層は同じ数の`neurons`を含みます。モデルへの入力としては、解釈を容易にするために最大2つの共変量を使用することをお勧めします。

# 引数:

  * `covariate_idx::Union{AbstractVector{<:Int}, Int}`: ブランチで使用する共変量のインデックス。
  * `neurons::Int`: 隠れ層のニューロンの数。
  * `heads::Int`: 独立したヘッドの数。
  * `activation`: 隠れ層で使用する活性化関数。デフォルト = swish。
  * `init_bias`: バイアスパラメータの初期化関数。デフォルト = ones32。初期推定を改善するのに役立ちます。
