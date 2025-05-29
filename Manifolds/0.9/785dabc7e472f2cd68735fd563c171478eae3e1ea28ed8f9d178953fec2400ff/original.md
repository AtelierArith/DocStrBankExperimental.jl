```
project(
    M::AbstractMultinomialDoublyStochastic,
    p;
    maxiter = 100,
    tolerance = eps(eltype(p))
)
```

project a matrix `p` with positive entries applying Sinkhorn's algorithm. Note that this project method – different from the usual case, accepts keywords.
