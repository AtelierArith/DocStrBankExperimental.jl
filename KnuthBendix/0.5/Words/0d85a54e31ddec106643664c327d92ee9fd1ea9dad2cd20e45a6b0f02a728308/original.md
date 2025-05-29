```
Word{T} <: AbstractWord{T}
```

Word as written in an alphabet storing only letters indices in an Alphabet.

The letters are stored in a plain `Vector{T}` field.

If type is not specified in the constructor it will default to `UInt16`.
