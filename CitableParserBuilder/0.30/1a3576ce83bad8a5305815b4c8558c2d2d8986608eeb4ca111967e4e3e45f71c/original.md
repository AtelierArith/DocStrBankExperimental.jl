Read a list of tokens from file `f` and parse with `p`.

```julia
parselist(f, p, reader; countinterval)

```

Returns a Dict mapping strings to a (possibly empty) vector of `Analysis` objects.
