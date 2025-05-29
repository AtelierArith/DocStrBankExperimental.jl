`Xcorr([domainType=Float64::Type,] dim_in::Tuple, h::AbstractVector)`

`Xcorr(x::AbstractVector, h::AbstractVector)`

Creates a `LinearOperator` which, when multiplied with an array `x::AbstractVector`, returns the cross correlation between `x` and `h`. Uses `xcross`. 
