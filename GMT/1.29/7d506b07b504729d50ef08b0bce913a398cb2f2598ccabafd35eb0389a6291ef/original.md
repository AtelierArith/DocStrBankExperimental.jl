```
hampel!(y, x, K; spread=mad, threshold=2)
hampel!(y, x, weights; ...)
```

Apply a weighted Hampel filter in-place.

The idiom `hampel!(x, x,...)` will make the filter recursive, i.e., vector elements are replaced as they are found, possibly affecting future results.
