```
fastgensphere(N::Int64, d::Int64; par::Bool=true)
```

A faster way to generate lds of length N on a d dimension unit sphere.

Similar to `gensphere()`. This function is much faster and support parallelism,  but may degenarate when d is large.
