```
(trace, lml_est) = importance_resampling(model::GenerativeFunction,
    model_args::Tuple, observations::ChoiceMap, num_samples::Int;
    verbose=false)

(traces, lml_est) = importance_resampling(model::GenerativeFunction,
    model_args::Tuple, observations::ChoiceMap,
    proposal::GenerativeFunction, proposal_args::Tuple,
    num_samples::Int; verbose=false)
```

サンプリング重要度再サンプリングを実行し、単一のトレースを返します。

`importance_sampling`とは異なり、使用されるメモリはサンプル数に対して一定です。

`verbose=true`を設定すると、各サンプルごとに進行メッセージが表示されます。
