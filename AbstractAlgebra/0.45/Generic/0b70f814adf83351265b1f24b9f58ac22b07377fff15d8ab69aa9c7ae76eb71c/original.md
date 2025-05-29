```
upscale(a::Generic.LaurentSeriesElem{T}, n::Int) where T <: RingElement
```

Deflate the underlying polynomial by a factor of $n$. This removes zero coefficients that existed for padding. It is assumed that the spacing of nonzero coefficients of $a$ is divisible by $n$.
