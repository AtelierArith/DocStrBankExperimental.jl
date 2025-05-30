```
get_vector(emb::IndexedWordEmbedding, query::String)
```

`get_vector()` は、指定されたトークン `query` の埋め込みベクトル (Float32) を返します。辞書ではなく、埋め込みオブジェクトで呼び出されます。型が安定しており、埋め込みベクトルのビューを返すか、例外をスローします。
