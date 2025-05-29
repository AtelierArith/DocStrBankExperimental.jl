```
NGramIterator{T}
```

整数のコレクション `s` の ngram コードを [`Mill.string_start_code()`](@ref) と [`Mill.string_end_code()`](@ref) を使用してパディングしながら反復します。NGram コードは、`s` のアイテムが桁、`b` が基数、`m` が剰余である位置数システムのように計算されます。

異なる順序の ngram を混合する際の衝突を減らすために、`s` にゼロや負の整数を避け、基数 `b` を `s` のユニークトークンの予想数に設定するべきです。

関連情報: [`NGramMatrix`](@ref), [`ngrams`](@ref), [`ngrams!`](@ref), [`countngrams`](@ref), [`countngrams!`](@ref).
