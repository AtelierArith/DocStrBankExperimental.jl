```
(model::CovGaussianNetwork)(state::AbstractArray, action::AbstractArray)
```

モデルが`state`にいるときに`action`をサンプリングする際のlogpdfを返します。Stateは`(state_size x 1 x batchsize)`の次元を持つ3Dテンソルでなければなりません。複数のアクションが各状態で取られる可能性があり、`action`は`(action_size x action_samples_per_state x batchsize)`の次元を持たなければなりません。`(1 x action_samples_per_state x batchsize)`の次元を持つ3Dテンソルを返します。
