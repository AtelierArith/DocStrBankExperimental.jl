```
read_indexed_emb(path::AbstractString)::WordEmbedding
```

The function reads indexed word embeddings from local binary embedding table files in `.jld2` and `.iem` formats. These files are Julia binary files that contain an `IndexedWordEmbedding` object under the name `"embedding"`.
