```
SequenceTokenizer{T, V <: AbstractVector{T}}
```

A struct for tokenizing sequences of symbols into numerical indices.

# Fields

  * `alphabet::V`: The set of valid symbols in the sequences
  * `lookup::Vector{UInt32}`: A lookup table for fast symbol-to-index conversion
  * `unksym::T`: The symbol to use for unknown tokens
  * `unkidx::UInt32`: The index assigned to the unknown symbol

# Example

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
```
