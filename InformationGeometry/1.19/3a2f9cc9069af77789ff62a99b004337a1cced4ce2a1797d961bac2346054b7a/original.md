```
SaveConfidence(sols::AbstractVector{<:AbstractODESolution}, N::Int=500; sigdigits::Int=7, adaptive::Bool=true) -> Matrix
SaveConfidence(Planes::AbstractVector{<:Plane}, sols::AbstractVector{<:AbstractODESolution}, N::Int=500; sigdigits::Int=7, adaptive::Bool=true) -> Matrix
```

Returns a `Matrix` of with `N` rows corresponding to the number of evaluations of each `ODESolution` in `sols`. The colums correspond to the various components of the evaluated solutions. E.g. for an `ODESolution` with 3 components, the 4. column in the `Matrix` corresponds to the evaluated first components of `sols[2]`.
