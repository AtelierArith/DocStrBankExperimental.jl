```
(tokenizer::SequenceTokenizer{T})(input::AbstractString) where T
```

Tokenize a string input using the SequenceTokenizer.

This method efficiently converts the input string to a vector of tokens of type T and applies the tokenizer to each element.

# Arguments

  * `tokenizer::SequenceTokenizer{T}`: The tokenizer to use
  * `input::AbstractString`: The input string to be tokenized

# Returns

A Vector{UInt32} of token indices corresponding to the characters in the input string

# Performance Notes

  * This method uses `collect(T, input)` to convert the string to a vector of type T
  * It's marked as `@inline` for potential performance benefits in certain contexts

# Example

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
result = tokenizer("abcx")
println(result)  # Output: [2, 3, 4, 1]
```
