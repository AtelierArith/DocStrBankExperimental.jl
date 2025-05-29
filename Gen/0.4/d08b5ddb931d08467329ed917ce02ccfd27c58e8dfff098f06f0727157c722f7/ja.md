```
(elbo_estimate, traces, elbo_history) = black_box_vi!(
    model::GenerativeFunction, model_args::Tuple,
    [model_update::ParamUpdate,]
    observations::ChoiceMap,
    var_model::GenerativeFunction, var_model_args::Tuple,
    var_model_update::ParamUpdate;
    options...)
```

与えられた `model` と `observations` によって示される事後分布に対して、変分モデル（`var_model`）のパラメータを確率的勾配法を使用して適合させます。ユーザーはオプションで `model_update` を指定して、`model` のパラメータを共同で更新することができます。

# 追加の引数:

  * `iters=1000`: 勾配降下の反復回数。
  * `samples_per_iter=100`: 単一の勾配ステップの前に勾配を蓄積するために変分モデルと生成モデルから取得するサンプルの数。
  * `verbose=false`: `true` の場合、適合の進行状況に関する情報を表示します。
  * `callback`: `(iter, traces, elbo_estimate)` を入力として受け取るコールバック関数で、`iter` は反復番号、`traces` はその反復のための `var_model` からのサンプルです。
