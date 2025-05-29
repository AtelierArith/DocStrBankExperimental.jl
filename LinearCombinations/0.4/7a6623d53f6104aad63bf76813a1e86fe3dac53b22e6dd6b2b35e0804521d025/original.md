```
has_char2(::Type{R}) where R -> Bool
```

Return `true` if the ring `R` is known to have characteristic `2` and `false` otherwise.

By default, `has_char2` returns `false` for all arguments. Changing it to `true` for a ring `R` avoids (possibly expensive) sign computations.

See also [`is_domain`](@ref).
