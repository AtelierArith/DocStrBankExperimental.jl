```julia
mutable struct CartesianState{F, LU, TU, AU} <: GeneralAstrodynamics.States.StateVector{F, LU, TU, AU, (x = 1, y = 2, z = 3, ẋ = 4, ẏ = 5, ż = 6, r = 1:3, v = 4:6)}
```

A Cartesian state vector with length 6. Internally uses `MVector` and `LVector` to store data. Data is accessible via labels, which are `x, y, z, ẋ, ẏ, ż, r, v`, where `r`  access `x,y,z` and `v` accesses `ẋ, ẏ, ż`.
