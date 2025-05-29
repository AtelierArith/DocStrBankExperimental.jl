```
HaltonSeq(base, length, skip=5000, f=identity)
```

Iterator generates a Halton sequence of `Rational{Int}`s  given a prime `base` and `length`, and skipping the first `skip` elements. Function `f`, such as `StatsFuns::norminvcdf`, can be used to transform a Halton draw into a quasi-random draw from a distribution

The algorithm is presented in Kolar & O'Shea (1993), [https://doi.org/10.1016/0898-1221(93)90307-H](https://doi.org/10.1016/0898-1221(93)90307-H) uses  `Vector`s `d` and `r` to keep track of intermediate computations. 
