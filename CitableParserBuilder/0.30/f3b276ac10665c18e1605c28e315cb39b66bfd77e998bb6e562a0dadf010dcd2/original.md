Read a list of tokens from URL `u` and parse with `p`.

```julia
parselist(u, p, reader; countinterval)

```

Returns a Dict mapping strings to a (possibly empty) vector of `Analysis` objects.
