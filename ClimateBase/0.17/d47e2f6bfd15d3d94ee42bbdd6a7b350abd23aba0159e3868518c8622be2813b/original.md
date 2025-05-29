```
lonlatfirst(A::ClimArray, args...) → B
```

Permute the dimensions of `A` to make a new array `B` that has first dimension longitude, second dimension latitude, with the remaining dimensions of `A` following (useful for most plotting functions). Optional extra dimensions can be given as `args...`, specifying a specific order for the remaining dimensions.

Example:

```julia
B = lonlatfirst(A)
C = lonlatfirst(A, Time)
```
