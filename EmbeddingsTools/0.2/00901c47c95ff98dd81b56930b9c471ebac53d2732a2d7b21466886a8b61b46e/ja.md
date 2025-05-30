```
limit(emb::IndexedWordEmbedding, n::Integer)::IndexedWordEmbedding
```

`limit()` 関数は、既存のインデックス付き単語埋め込みのコピーを作成し、最初の `n` トークンのみを含みます。この関数は、`read_embedding()` で `max_vocab_size` 引数を使用するのと似ています。ただし、`read_vec()` + `limit()` または `read_vec()` + `subspace()` を使用する方が、一般的に `max_vocab_size` または `keep_words` 引数を使用するよりも速いです。
