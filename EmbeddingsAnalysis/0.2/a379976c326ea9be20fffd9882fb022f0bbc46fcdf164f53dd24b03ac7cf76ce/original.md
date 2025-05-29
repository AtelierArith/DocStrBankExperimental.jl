```
compressedwordvectors(filename [,type=Float64][; kind=:text])
```

Generate a `CompressedWordVectors` type object from a file.

# Arguments

  * `filename::AbstractString` the embeddings file name
  * `type::Type` type of the embedding vector elements; default `Float64`

# Keyword arguments

  * `kind::Symbol` specifies whether the embeddings file is textual (`:text`)

or binary (`:binary`); default `:text`
