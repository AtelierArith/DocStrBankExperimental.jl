```
CollocationPoint{N,CT} <: AbstractCollocationPoint{N,CT}
```

A collocation point.

# Fields

`i_multi::SVector{N,Int}` : The i-th item of this Vector represents to the level of the collocation point in the i-th dimension. `pt_idx::SVector{N,Int}` : The i-th item of this Vector represents to the point index of the collocation point in the i-th dimension. `coords::SVector{N,CT}` : Coordinates of the collocation point. `interv::SVector{N,SVector{2,CT}}` : The i-th item of the Vector defines the non-zero interval of the associated basis function in the i-th dimension.
