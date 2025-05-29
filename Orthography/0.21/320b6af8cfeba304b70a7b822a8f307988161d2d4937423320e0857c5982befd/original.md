Tokenize corpus `c` using the tokenizer of the given orthographic system.

```julia
tokenize(c, ortho; edition, exemplar)

```

The return value is a list of pairings of a `CitablePassage` and a token category.  The citable node is citable at the level of the token.
