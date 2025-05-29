```
inverse_document_frequencies(term_matrix)
```

スムーズな逆文書頻度を `log.((1 + ndocuments)./(1 .+ df)) .+ 1` として計算します。ここで `df` は文書頻度です。分子と分母の定数 `1` は、語彙内の各単語を一度含む追加の文書に対応し、ゼロ除算エラーを防ぎます。
