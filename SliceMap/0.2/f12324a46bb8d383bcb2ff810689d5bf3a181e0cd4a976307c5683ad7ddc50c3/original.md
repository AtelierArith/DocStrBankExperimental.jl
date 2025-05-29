```
mapcols(f, m) ≈ mapreduce(f, hcat, eachcol(m)) ≈ mapslices(f, m, dims=1)
```

This is a more efficient version of the functions on the right. For `f(x::Vector)::Matrix` it reshapes like `mapslices(vec∘f, m, dims=1)`. For `f(x::Vector)::Number` it skips the reduction, just `reshape(map(f, eachcol(m)),1,:)`.

It provides a gradient for Tracker and Zygote, saving the backward function for each slice.

Any arguments after the matrix are passed to `f` as scalars, i.e. `mapcols(f, m, args...) = reduce(hcat, f(col, args...) for col in eeachcol(m))`. They do not get sliced/iterated (unlike `map`), nor are their gradients tracked.

Note that if `f` itself contains parameters, their gradients are also not tracked.
