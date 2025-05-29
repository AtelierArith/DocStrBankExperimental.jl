Tokenize a corpus, and chunk the resulting vector of tokens by sentence. The result is a vector of `NamedTuple`s with a URN and a sequence number.  The URN is a range of tokens.

```julia
parsesentences(c, ortho; terminators)

```
