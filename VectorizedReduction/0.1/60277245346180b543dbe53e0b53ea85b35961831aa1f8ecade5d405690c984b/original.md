```
vtextrema([f=identity], A::AbstractArray, dims=:)
```

Compute the minimum and maximum values by calling `f` on each element of of `A` over the given `dims`. Threaded.
