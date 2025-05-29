```
(traces, log_norm_weights, lml_est) = importance_sampling(model::GenerativeFunction,
    model_args::Tuple, observations::ChoiceMap, num_samples::Int; verbose=false)

(traces, log_norm_weights, lml_est) = importance_sampling(model::GenerativeFunction,
    model_args::Tuple, observations::ChoiceMap,
    proposal::GenerativeFunction, proposal_args::Tuple,
    num_samples::Int; verbose=false)
```

重要度サンプリングを実行し、関連する対数重みを持つトレースのベクトルを返します。

対数重みは正規化されています。また、観測の周辺尤度の推定値（`lml_est`）も返します。観測は、指定されたモデル引数でモデルによってサンプリングされる必要があるアドレスです。最初のバリアントは、モデルの内部提案分布を使用します。2番目のバリアントは、指定された生成関数によって定義されたカスタム提案分布を使用します。提案によってサンプリングされたランダム選択のすべてのアドレスは、モデル関数によってもサンプリングされる必要があります。`verbose=true`を設定すると、サンプルごとに進行メッセージが表示されます。
