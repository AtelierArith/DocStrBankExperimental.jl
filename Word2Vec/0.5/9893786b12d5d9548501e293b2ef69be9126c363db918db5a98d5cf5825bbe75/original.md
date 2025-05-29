```
wordvectors(filename [,type=Float64][; kind=:text, skip=false, normalize=true, fasttext=false])
```

Generate a WordVectors type object from a file.

# Arguments

  * `filename::AbstractString` the embeddings file name
  * `type::Type` type of the embedding vector elements; default `Float64`

# Keyword arguments

  * `kind::Symbol` specifies whether the embeddings file is textual (`:text`)

or binary (`:binary`); default `:text`

  * `skip::Bool` in binary embeddings files specifies whether the newline

byte is missing or not (use `true` for Google pre-trained models); default `false`

  * `normalize:Bool` specifies whether to normalize the embedding vectors

i.e. return unit vectors; default `true`

  * `delim:Char` delimiter; default `' '`
  * `fasttext::Bool` setting to `true` fixes a bug that occurs when loading

FastText generated text embeddings by not stripping the line before parsing. The option is ignored for the binary format; default `false`
