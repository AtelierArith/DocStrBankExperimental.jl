```
(model::CovGaussianNetwork)(rng::AbstractRNG, state::AbstractArray{<:Any, 3}, action_samples::Int)
```

状態 `state` ごとに `action_samples` のアクションをサンプルし、`actions, logpdf(actions)` を返します。この関数は多次元アクション空間に対応しています。出力はそれぞれ `actions` と `logdpf` に対して `(action_size x action_samples x batchsize)` および `(1 x action_samples x batchsize)` の次元を持つ3Dテンソルです。
