```
mult_gauss(X; clip=false[, σ=0.1, μ=1])
```

Returns the array `X` with the array value multiplied with a gauss distribution (standard deviation `σ` and mean `μ`) .  `σ` and `μ` are optional arguments representing standard deviation and mean of gauss. If keyword argument `clip` is provided the values are clipped to be in [0, 1]. If `X` is a RGB{Normed} or Gray{Normed} image, then the values will be automatically clipped and the keyword  `clip` is meaningless.

If `X<:Complex`, `μ` and `σ` are applied to the imaginary in the same way as for the real part. If you want to have different behaviour for real and imaginary part, simply choose `μ` or `σ` complex.
