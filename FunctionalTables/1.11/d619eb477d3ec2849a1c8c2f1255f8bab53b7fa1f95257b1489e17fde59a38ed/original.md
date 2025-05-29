```julia
rename(ft, changes)

```

Rename the columns of a `FunctionalTable`. The second argument should be a `NamedTuple` of `src = dest` pairs, where `dest` is a symbol.

# Example

```julia
rename(ft, (α = :a, β = :b)) # rename `α` to `a` and `β` to `b`
```
