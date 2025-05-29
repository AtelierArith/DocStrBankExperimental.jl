```
dot_product_attention_scores(query, key, [bias]; [fdrop, mask])
```

[`dot_product_attention`](@ref) のためのアテンションスコアを返します。入力配列は `(num_features ÷ nheads, nheads, sequence_length, batch_size)` の次元を持たなければなりません。

詳細については [`dot_product_attention`](@ref) を参照してください。
