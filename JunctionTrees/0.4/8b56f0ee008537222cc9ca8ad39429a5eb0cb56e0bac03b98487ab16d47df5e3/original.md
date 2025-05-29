```julia
struct Factor{T, N}
```

# Fields

  * `vars`
  * `vals`

Encodes a discrete function over the set of variables `vars` that maps each instantiation of `vars` into a nonnegative number in `vals`.
