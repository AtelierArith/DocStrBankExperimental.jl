```
averageallindistance(radiusbin,array :: Array{T,2},mask,center,gridspacing = 1)
```

Create an average of the quantity in array at all the points located between radiusbin[1] and radiusbin[2] from a center. The points should be masked by a boolean array. It assumes a uniform gridspacing.
