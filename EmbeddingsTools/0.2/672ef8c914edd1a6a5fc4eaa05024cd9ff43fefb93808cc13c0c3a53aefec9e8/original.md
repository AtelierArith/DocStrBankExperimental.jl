```
read_vec(path::AbstractString; delim::AbstractChar=' ')::WordEmbedding
```

The function `read_vec()` is used to read a local embedding matrix from a text file (.txt, .vec, etc) at a given `path`. It creates a `WordEmbedding` object using the CSV.jl package. The delimiter used for the text file can be set using the `delim` parameter. This function is a simplified version of `read_embedding()` and it always reads in the entire embedding table, making the logic more straightforward.
