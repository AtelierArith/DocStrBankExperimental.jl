```
crosscorrcomplex(x::Vector{ComplexF64}, y::Vector{ComplexF64}, m::Int64; normed = false)

computes the cross correlation between *complex* vectors x and y (because the stats base function does NOT). For auto correlation, use x = y, and for normalization in that case set normed = true

Arguments
=================
- x: complex vector of length L
- y: complex vector of length L
- m: integer strictly less than l, number of nLags
- normed: whether or not to norm by the value when m = 0
```
