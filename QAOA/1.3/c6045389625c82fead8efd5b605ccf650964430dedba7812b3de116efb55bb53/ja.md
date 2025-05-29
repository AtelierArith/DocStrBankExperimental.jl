```
optimize_parameters(problem::Problem, beta_and_gamma::Vector{Float64}, algorithm; niter::Int=128)
```

QAOAコスト関数の勾配フリー最適化 `using NLopt`。

### 入力

  * `problem::Problem`: 最適化問題を定義する `Problem` インスタンス。
  * `beta_and_gamma::Vector{Float64}`: 初期QAOAパラメータのベクトル。
  * `algorithm`: [NLoptのアルゴリズム](https://nlopt.readthedocs.io/en/latest/NLopt_Algorithms/)の1つ。
  * `niter::Int=128` (オプション): 実行される最適化ステップの数。

### 出力

  * `cost`: コスト関数の最終値。
  * `params`: 最適化されたパラメータ。
  * `probabilities`: すべての可能な結果のシミュレーションされた確率。

### 例

  * 与えられた層の数 `p`、局所場 `h` および結合 `J` に対して、問題を定義します。

`problem = QAOA.Problem(p, h, J)` 

その後、次のようにします。

`cost, params, probs = QAOA.optimize_parameters(problem, ones(2p), :LN_COBYLA)`。
