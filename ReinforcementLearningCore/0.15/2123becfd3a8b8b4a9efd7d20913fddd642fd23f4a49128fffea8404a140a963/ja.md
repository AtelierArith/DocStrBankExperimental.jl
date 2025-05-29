```
(model::CategoricalNetwork)([rng::AbstractRNG,] state::AbstractArray{<:Any, 3}, [mask::AbstractArray{Bool},] action_samples::Int)
```

各状態から `action_samples` アクションをサンプリングします。次元が `(action_size x action_samples x batchsize)` の3Dテンソルを返します。常に同じ次元のテンソル内の各アクションの *logits* を返します。オプションの引数 `mask` は、最初の次元がアクションベクトルの長さであることを除いて、`state` と同じサイズの `Bool` の配列でなければなりません。マスクによって `false` にマッピングされたアクションは、`-Inf` に等しいlogitおよび/またはサンプリングされる確率がゼロになります。
