```
poisson(X; scaling=nothing, clip=false)
```

Returns the array `X` affected by Poisson noise.  At every position the Poisson noise affects the intensity individually  and the values at the positions represent the expected value of the Poisson Distribution.  Since Poisson Noise due to discrete events you should provide the optional argument `scaling`. This `scaling` connects the highest value of the array with the discrete number of events. The highest value will be then scaled and the poisson noise is applied Afterwards we scale the whole array back so that the initial intensity is preserved but with applied Poisson noise. `clip` is a keyword argument. If given, it clips the values to [0, 1]
