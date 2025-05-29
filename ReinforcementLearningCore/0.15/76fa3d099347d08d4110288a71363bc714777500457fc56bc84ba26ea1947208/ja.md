```
(model::CovGaussianNetwork)(rng::AbstractRNG, state::AbstractArray{<:Any, 3}, action_samples::Int)
```

状態 `state` ごとに `action_samples` のアクションをサンプリングし、`actions, logpdf(actions)` を返します。この関数は多次元アクション空間と互換性があります。出力はそれぞれ `actions` と `logdpf` に対して `(action_size x action_samples x batchsize)` および `(1 x action_samples x batchsize)` の次元を持つ3Dテンソルです。
