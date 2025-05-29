```
normalise(x; dims=ndims(x), ϵ=1e-5)
```

Normalise the array `x` to mean 0 and standard deviation 1 across the dimension(s) given by `dims`. Per default, `dims` is the last dimension. 

`ϵ` is a small additive factor added to the denominator for numerical stability.
