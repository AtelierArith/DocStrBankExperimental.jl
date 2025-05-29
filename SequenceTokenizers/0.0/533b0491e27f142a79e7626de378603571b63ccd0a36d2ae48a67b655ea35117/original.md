```
(tokenizer::SequenceTokenizer{T})(x::AbstractArray) where T
```

Tokenize an array of symbols.

# Arguments

  * `x::AbstractArray`: An array of symbols to be tokenized

# Returns

An array of indices corresponding to the input symbols

# Example

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
println(tokenizer(['a', 'b', 'z', 'c']))  # Output: [2, 3, 1, 4]
```
