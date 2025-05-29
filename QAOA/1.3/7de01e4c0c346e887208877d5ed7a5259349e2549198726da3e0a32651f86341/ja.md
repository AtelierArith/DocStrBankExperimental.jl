```
optimize_parameters(problem::Problem, beta_and_gamma::Vector{Float64}; niter::Int=128, learning_rate::Float64 = 0.05)
```

QAOAコスト関数の勾配最適化 `using Zygote`。

### 入力

  * `problem::Problem`: 最適化問題を定義する `Problem` インスタンス。
  * `beta_and_gamma::Vector{Float64}`: 初期QAOAパラメータのベクトル。
  * `niter::Int=128` (オプション): 実行される最適化ステップの数。
  * `learning_rate::Float64=0.05` (オプション): 勾配上昇法の学習率。

### 出力

  * `cost`: コスト関数の最終値。
  * `params`: 最適化されたパラメータ。
  * `probabilities`: すべての可能な結果のシミュレーションされた確率。

### 注意事項

  * 勾配上昇法はパラメータ更新を通じて定義されます

`params = params .+ learning_rate .* gradient(f, params)[1]`。

### 例

  * 与えられた層の数 `p`、局所場 `h` および結合 `J` に対して、問題を定義します

`problem = QAOA.Problem(p, h, J)` 

その後、次のようにします

`cost, params, probs = QAOA.optimize_parameters(problem, ones(2p))`。
