```
BPELearner(tokenization::AbstractTokenization; min_freq = 10, endsym = "</w>", sepsym = nothing)
```

`BPETokenization` と `NoBPE` を含む `tokenization` を持つ学習者を構築します。

```
(bper::BPELearner)(word_counts, n_merge)
```

[`count_words`](@ref) によって作成された `word_counts` 辞書で学習者を呼び出すと、`NoBPE` が学習された `BPE` に置き換えられた新しい `tokenization` が生成されます。
