```
(tokenizer::SequenceTokenizer{T})(token::T) where T
```

Convert a single token to its corresponding index.

# Arguments

  * `token::T`: A single token to be converted to an index

# Returns

The index of the token in the tokenizer's alphabet, or the unknown token index if not found

# Example

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
println(tokenizer('a'))  # Output: 2
println(tokenizer('x'))  # Output: 1
println(tokenizer('z'))  # Output: 1 (unknown token)
```
