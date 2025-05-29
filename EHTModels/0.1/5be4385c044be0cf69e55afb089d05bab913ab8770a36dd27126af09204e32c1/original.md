```
visanalytic(::Type{<:AbstractModel})
```

Determines whether the model is pointwise analytic in Fourier domain, i.e. we can evaluate its fourier transform at an arbritrary point. If `IsAnalytic()` then it will try to call `visibility_point` to calculate the complex visibilities. Otherwise it fallback to using the FFT that works for all models that can compute an image.
