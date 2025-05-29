```
vtminimum(f, A; dims=:, init=typemax)
```

Compute the minimum value of calling `f` on each element of `A` over the given `dims`, with the min initialized by `init`, which may be a value `<:Number` or a function which accepts a single type argument.
