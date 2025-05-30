```
limit(emb::AbstractEmbedding, n::Integer)::WordEmbedding
```

The `limit()` function creates a copy of an existing word embedding, containing only the first `n` tokens. This function is similar to using a `max_vocab_size` argument in `read_embedding()`. However, using `read_vec()` + `limit()` or `read_vec()` + `subspace()` is generally faster than using `max_vocab_size` or `keep_words` arguments, respectively.
