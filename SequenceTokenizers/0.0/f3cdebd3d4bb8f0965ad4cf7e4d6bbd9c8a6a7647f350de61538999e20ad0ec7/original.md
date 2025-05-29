```
(tokenizer::SequenceTokenizer{T})(batch::AbstractVector{<:AbstractVector{T}}) where T
```

Tokenize a batch of sequences, padding shorter sequences with the unknown token.

# Arguments

  * `batch::AbstractVector{<:AbstractVector{T}}`: A vector of sequences to be tokenized

# Returns

A matrix of indices, where each column represents a tokenized and padded sequence

# Example

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
sequences = [['a', 'b'], ['c', 'a', 'b']]
println(tokenizer(sequences))
# Output:
# [2 4
#  3 2
#  1 3]
```
