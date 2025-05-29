`Conv([domainType=Float64::Type,] dim_in::Tuple, h::AbstractVector)`

`Conv(x::AbstractVector, h::AbstractVector)`

Creates a `LinearOperator` which, when multiplied with an array `x::AbstractVector`, returns the convolution between `x` and `h`. Uses `conv` and hence FFT algorithm. 
