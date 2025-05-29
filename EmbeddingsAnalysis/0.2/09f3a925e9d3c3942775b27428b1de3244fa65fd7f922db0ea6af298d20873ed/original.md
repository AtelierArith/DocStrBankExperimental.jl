```
write2disk(filename::AbstractString, wv::CompressedWordVectors [;kind=:binary])
```

Writes compressed embeddings to disk.

# Arguments

  * `filename::AbstractString` the embeddings file name
  * `wv::CompressedWordVectors` the embeddings

# Keyword arguments

  * `kind::Symbol` specifies whether the embeddings file is textual (`:text`)

or binary (`:binary`); default `:binary`
