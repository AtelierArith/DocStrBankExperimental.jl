Orientation selective frequency domain filter with Gaussian windowing function.

```
Usage: filter = gaussianangularfilter(angl, thetaSigma, sintheta, costheta)

Arguments:
               angl - Orientation of the filter (radians)
         thetasigma - Standard deviation of angular Gaussian window function.
 sintheta, costheta - Grids as returned by gridangles()
```

See also: [`cosineangularfilter`](@ref), [`gridangles`](@ref), [`filtergrids`](@ref)
