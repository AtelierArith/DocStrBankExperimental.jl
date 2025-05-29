```
(iwelbo_estimate, traces, iwelbo_history) = black_box_vimco!(
    model::GenerativeFunction, model_args::Tuple,
    [model_update::ParamUpdate,]
    observations::ChoiceMap,
    var_model::GenerativeFunction, var_model_args::Tuple,
    var_model_update::ParamUpdate,
    grad_est_samples::Int; options...)
```

与えられた `model` と `observations` によって示される事後分布に対して、変分モデル (`var_model`) のパラメータを適合させるために、[Variational Inference with Monte Carlo Objectives](https://arxiv.org/abs/1602.06725) (VIMCO) の周辺尤度に対する下限に適用される確率的勾配法を使用します。ユーザーは、`model` のパラメータを共同で更新するために `model_update` を指定することもできます。

# 追加の引数:

  * `grad_est_samples::Int`: VIMCO勾配推定のためのサンプル数。
  * `iters=1000`: 勾配降下の反復回数。
  * `samples_per_iter=100`: 単一の勾配ステップの前に勾配を蓄積するための変分モデルと生成モデルからのサンプル数。
  * `geometric=true`: [Variational Inference with Monte Carlo Objectives](https://arxiv.org/abs/1602.06725) で説明されている幾何学的または算術的ベースラインを使用するかどうか。
  * `verbose=false`: `true` の場合、適合の進行状況に関する情報を印刷します。
  * `callback`: `(iter, traces, elbo_estimate)` を入力として受け取るコールバック関数で、`iter` は反復番号、`traces` はその反復のための `var_model` からのサンプルです。
