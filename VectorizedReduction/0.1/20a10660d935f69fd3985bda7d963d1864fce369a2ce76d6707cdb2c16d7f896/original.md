```
vvprod(f, A; dims=:, init=one)
```

Multiply the results of calling `f` on each element of `A` over the given `dims`, with the product initialized by `init`, which may be a value `<:Number` or a function which accepts a single type argument.
