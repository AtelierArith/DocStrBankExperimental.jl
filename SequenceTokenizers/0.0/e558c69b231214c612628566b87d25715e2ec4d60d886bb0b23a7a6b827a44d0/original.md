```
(tokenizer::SequenceTokenizer)(idx::Integer)
```

Convert an index back to its corresponding token.

# Arguments

  * `idx::Integer`: An index to be converted back to a token

# Returns

The token corresponding to the given index in the tokenizer's alphabet

# Example

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
println(tokenizer(2))  # Output: 'a'
println(tokenizer(1))  # Output: 'x' (unknown token)
```
