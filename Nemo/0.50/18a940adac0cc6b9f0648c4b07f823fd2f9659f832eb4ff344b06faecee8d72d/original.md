```
downscale(a::ZZLaurentSeriesRingElem, n::Int)
```

Inflate the underlying polynomial by a factor of $n$. This inserts zero coefficients for padding. It is assumed that the scale factor of $a$ is divisible by $n$.
