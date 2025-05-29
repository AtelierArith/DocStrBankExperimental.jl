```
(model::GaussianNetwork)(rng::AbstractRNG, state::AbstractArray{<:Any, 3}, action_samples::Int)
```

各状態から `action_samples` アクションをサンプリングします。返されるのは、次元が `(action_size x action_samples x batchsize)` の 3D テンソルです。`state` は次元が `(state_size x 1 x batchsize)` の 3D テンソルでなければなりません。常に各アクションの logpdf を返します。
