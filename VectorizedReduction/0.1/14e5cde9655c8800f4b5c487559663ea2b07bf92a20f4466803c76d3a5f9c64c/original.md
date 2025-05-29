```
vcount([f=identity,] A::AbstractArray, dims=:)
```

Count the number of elements in `A` for which `f` return true over the given `dims`. If `f` is omitted, count the number of `true` elements in `A` (which should be `AbstractArray{Bool}`).
