Given a function `f` defined on the interval `[x1, x2]`, subdivide the interval into `n` equally spaced segments, and search for zero crossings of the function. `nroot` will be set to the number of bracketing pairs found. If it is positive, the arrays `xb1[1..nroot]` and `xb2[1..nroot]` will be filled sequentially with any bracketing pairs that are found.

##### Arguments

  * `f::Function`: The function you want to bracket
  * `x1::T`: Lower border for search interval
  * `x2::T`: Upper border for search interval
  * `n::Int(50)`: The number of sub-intervals to divide `[x1, x2]` into

##### Returns

  * `x1b::Vector{T}`: `Vector` of lower borders of bracketing intervals
  * `x2b::Vector{T}`: `Vector` of upper borders of bracketing intervals

##### References

This is `zbrack` from Numerical Recepies Recepies in C++
