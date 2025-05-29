```
convolve!(img::IntensityMap, m::AbstractModel)
```

Convolves an `img` with a given analytic model `m`. This is useful for blurring the image with some model. For instance to convolve a image with a Gaussian you would do

```julia
convolve!(img, Gaussian())
```

# Notes

This method does not automatically pad your image. If there is substantial flux at the boundaries you will start to see artifacts.
