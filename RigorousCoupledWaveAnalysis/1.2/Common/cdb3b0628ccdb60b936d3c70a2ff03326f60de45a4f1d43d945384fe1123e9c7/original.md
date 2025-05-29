```
recip2real(dnx,dny,F)
recip2real(dnx,dny,F,sx,sy)
```

Converts a reciprocal space convolution matrix into a 2D real space pattern. sx and sy can be specified to increase the image resolution. If not specified, an fft is carried out directly, and the result has the same size as the reciprocal space representation.

# Arguments

  * `dnx` : reciprocal space grid in x
  * `dny` : reciprocal space grid in y
  * `F`: reciprocal space convolution matrix
  * `sx`: number of pixels in the result along the x axis
  * `sy`: number of pixels in the result along the y axis

# Output

  * `f` : binary real-space representation corresponding to F
