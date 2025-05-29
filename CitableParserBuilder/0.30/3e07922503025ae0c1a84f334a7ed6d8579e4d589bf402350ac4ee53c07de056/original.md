Parse a list of tokens with a `CitableParser`.

```julia
parselist(vocablist, p; countinterval)

```

Returns a Dict mapping strings to a (possibly empty) vector of `Analysis` objects. Blank lines in input are silently ignored.
