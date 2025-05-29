```
write2disk(filename::AbstractString, wv::WordVectors [;kind=:binary])
```

Writes embeddings to disk.

# Arguments

  * `filename::AbstractString` the embeddings file name
  * `wv::WordVectors` the embeddings

# Keyword arguments

  * `kind::Symbol` specifies whether the embeddings file is textual (`:text`)

or binary (`:binary`); default `:binary`
