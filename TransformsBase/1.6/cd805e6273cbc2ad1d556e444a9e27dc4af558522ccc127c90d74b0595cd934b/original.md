```
isrevertible(transform)
```

Tells whether or not the `transform` is revertible, i.e. supports a [`revert`](@ref) function. Defaults to `false` for new transform types.

Transforms can be revertible and yet don't be invertible. Invertibility is a mathematical concept, whereas revertibility is a computational concept.

See also [`isinvertible`](@ref).
