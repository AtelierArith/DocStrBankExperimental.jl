```
(model::GaussianNetwork)(rng::AbstractRNG, state::AbstractArray{<:Any, 3}, action_samples::Int)
```

各状態から `action_samples` アクションをサンプリングします。返されるのは、次元が `(action_size x action_samples x batchsize)` の3Dテンソルです。`state` は次元が `(state_size x 1 x batchsize)` の3Dテンソルでなければなりません。常に各アクションの対数確率密度関数を返します。
