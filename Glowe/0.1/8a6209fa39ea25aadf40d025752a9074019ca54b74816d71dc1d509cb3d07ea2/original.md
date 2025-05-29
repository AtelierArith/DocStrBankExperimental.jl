```
wordvectors(filename [,type=Float64][; kind=:text, header=false, normalize=true, vocabulary=nothing])
```

Generate a WordVectors type object from a file.

# Arguments

  * `filename::AbstractString` the embeddings file name
  * `type::Type` type of the embedding vector elements; default `Float64`

# Keyword arguments

  * `kind::Symbol` specifies whether the embeddings file is textual (`:text`)

or binary (`:binary`); default `:text`

  * `header::Union{Nothing, Bool}` in text embeddings files specifies

whether the file contains a header i.e. number of lines, columns or not.   If the header is `nothing`, the loader will attempt to autodetect the   presence of a header; default `nothing`

  * `normalize:Bool` specifies whether to normalize the embedding vectors

i.e. return unit vectors; default true

  * `vocabulary::Union{Nothing, AbstractString}` path to the vocabulary

file generated with `vocab_count` (needed for binary embeddings); default `nothing`

  * `load_bias::Bool` specifies whether to load the bias term or not

if using binary embedding files; default `false`
