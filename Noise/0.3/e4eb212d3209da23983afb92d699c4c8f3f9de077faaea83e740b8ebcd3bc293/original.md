```
mult_gauss_chn(X; clip=false[, σ=0.1, μ=0.0])
```

Returns the RGB image `X` with the values of the pixel multiplied with a gauss distribution (standard deviation `σ` and mean `μ`) pixelwise.  However, every channel of one pixel receives the same amount of noise. The noise therefore acts roughly as intensity - but not color - changing noise. If keyword argument `clip` is provided the values are clipped to be in [0, 1]. `σ` and `μ` are optional arguments representing standard deviation and mean of gauss.

If `X<:Complex`, `μ` and `σ` are applied to the imaginary in the same way as for the real part. If you want to have different behaviour for real and imaginary part, simply choose `μ` or `σ` complex.
