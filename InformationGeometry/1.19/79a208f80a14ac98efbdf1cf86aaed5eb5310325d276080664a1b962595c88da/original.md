```
SaveGeodesics(sols::AbstractVector{<:AbstractODESolution}, N::Int=500; sigdigits::Int=7, adaptive::Bool=true) -> Matrix
```

Returns a `Matrix` of with `N` rows corresponding to the number of evaluations of each `ODESolution` in `sols`. The colums correspond to the various components of the evaluated solutions. Since the solution objects for geodesics contain the velocity as the second half of the components, only the first half of the components is saved.
