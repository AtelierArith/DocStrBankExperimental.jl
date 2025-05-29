```
(tokenizer::SequenceTokenizer{T})(batch::AbstractVector{<:AbstractString}) where T
```

Tokenize a batch of string sequences, padding shorter sequences with the unknown token.

# Arguments

  * `tokenizer::SequenceTokenizer{T}`: The tokenizer to use
  * `batch::AbstractVector{<:AbstractString}`: A vector of string sequences to be tokenized

# Returns

A matrix of indices, where each column represents a tokenized and padded sequence

# Example

```julia
tokenizer = SequenceTokenizer(['A','T','G','C'], 'N')
sequences = ["ATG", "ATGCGC"]
result = tokenizer(sequences)
```
