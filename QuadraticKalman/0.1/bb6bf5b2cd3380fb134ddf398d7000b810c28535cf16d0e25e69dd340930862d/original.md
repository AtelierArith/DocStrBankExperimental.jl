```
QKData(Y::AbstractArray{T,N}) where {T<:Real, N}
```

Construct a `QKData{T,N}` from the array `Y`. 

# Arguments

  * `Y::AbstractArray{T,N}`: Input array (vector or matrix)

# Returns

  * `QKData{T,N}`: Validated data structure

# Description

For vector input (N=1):

  * M is set to 1
  * T_bar is length(Y) - 1

For matrix input (N=2):

  * M is first dimension size
  * T_bar is second dimension size minus 1
