```
upscale(a::ZZLaurentSeriesRingElem, n::Int)
```

Deflate the underlying polynomial by a factor of $n$. This removes zero coefficients that were inserted for padding. It is assumed that the spacing between nonzero coefficients of $a$ is divisible by $n$.
