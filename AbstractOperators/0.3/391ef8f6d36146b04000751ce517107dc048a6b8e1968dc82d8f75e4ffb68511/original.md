`Filt([domainType=Float64::Type,] dim_in::Tuple, b::AbstractVector, [a::AbstractVector,])`

`Filt(x::AbstractVector, b::AbstractVector, [a::AbstractVector,])`

Creates a `LinearOperator` which, when multiplied with an array `x::AbstractVector`, returns a vector `y` filtered by an IIR filter of coefficients `b` and `a`. If only `b` is provided a FIR is used to comute `y` instead. 
