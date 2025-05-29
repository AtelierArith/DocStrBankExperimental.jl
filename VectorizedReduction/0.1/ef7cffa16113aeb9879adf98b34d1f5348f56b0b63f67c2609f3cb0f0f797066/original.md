```
vvsum(f, A; dims=:, init=zero)
```

Sum the results of calling `f` on each element of `A` over the given `dims`, with the sum initialized by `init`, which may be a value `<:Number` or a function which accepts a single type argument.
