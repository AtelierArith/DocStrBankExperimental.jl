```
isinvertible(transform)
```

Tells whether or not the `transform` is invertible, i.e. whether it implements the `inverse` function. Defaults to `false` for new transform types.

Transforms can be invertible in the mathematical sense, i.e., there exists a one-to-one mapping between input and output spaces.

See also [`inverse`](@ref), [`isrevertible`](@ref).
