```
hemispheric_means(A [,W]) → nh, sh
```

Return the (proper) averages of `A` over the northern and southern hemispheres. Notice that this function explicitly does both zonal as well as meridional averaging. Use [`hemispheric_functions`](@ref) to just split `A` into two hemispheres.

Optionally provide weights `W` that need to have the same structure as [`spaceagg`](@ref).
