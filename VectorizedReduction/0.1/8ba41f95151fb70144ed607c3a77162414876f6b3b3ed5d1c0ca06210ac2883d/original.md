```
vvmaximum(f, A; dims=:, init=typemin)
```

Compute the maximum value of calling `f` on each element of `A` over the given `dims`, with the max initialized by `init`, which may be a value `<:Number` or a function which accepts a single type argument.
