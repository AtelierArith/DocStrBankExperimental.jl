```
read_emb(path::AbstractString)::WordEmbedding
```

The function reads word embeddings from local binary embedding table files in `.jld` and `.emb` formats. These files are Julia binary files that contain a `WordEmbedding` object under the name `"embedding"`.
