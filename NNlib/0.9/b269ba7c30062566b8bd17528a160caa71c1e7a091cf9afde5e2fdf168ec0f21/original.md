```
dot_product_attention_scores(query, key, [bias]; [fdrop, mask])
```

Return the attention scores for the [`dot_product_attention`](@ref). Input arrays must have dimensions `(num_features ÷ nheads, nheads, sequence_length, batch_size)`.

See [`dot_product_attention`](@ref) for more details.
