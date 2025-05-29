```julia
mutable struct TokenStream
```

Tokenstream allows to read tokenized data from file without keeping the file ocntent in memory.

  * `input::IOStream`: Input stream

  * `tokens::Vector{SubString{String}}`: Array of current tokens kept in memory.

  * `itoken::Int64`: Position of actual token in tokens array

  * `lineno::Int64`: Line number in IOStream

  * `comment::Char`: Comment character

  * `dlm::Function`: Function telling if given character is a delimiter.
