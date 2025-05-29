```
second_moment(im::AbstractIntensityMap; center=true)
```

Computes the image second moment tensor of the image. By default we really return the second **cumulant** or centered second moment, which is specified by the `center` argument.

For polarized maps we return the second moment for Stokes I only.
