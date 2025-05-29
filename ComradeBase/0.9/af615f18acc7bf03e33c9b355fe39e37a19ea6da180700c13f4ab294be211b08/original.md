```
second_moment(im::IntensityMap; center=true)
```

Computes the image second moment tensor of the image. By default we really return the second **cumulant** or centered second moment, which is specified by the `center` argument.
