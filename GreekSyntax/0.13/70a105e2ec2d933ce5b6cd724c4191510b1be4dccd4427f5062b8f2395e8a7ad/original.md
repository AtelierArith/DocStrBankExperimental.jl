Tokenize a vector of analyzed tokens, and chunk by sentence. The result is a vector of `NamedTuple`s with a URN and a sequence number.  The URN is a range of tokens.

```julia
parsesentences(v, ortho; terminators)

```
