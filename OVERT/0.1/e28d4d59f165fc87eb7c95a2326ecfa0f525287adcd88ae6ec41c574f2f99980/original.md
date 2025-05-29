```
overapprox(expr,
              range_dict::Dict{Symbol, Array{T, 1}} where {T <: Real};
              N::Integer=2,
              ϵ::Real=1e-2)
-> OverApproximation
```

Overapproximate an n-dimensional function using a relational abstraction.

N    is the number of linear segments used per region of constant convexity. To allow OVERT to automatically choose this number, set N to -1. It will add segments until the maximum deviation between the function and the bound is within the relative error tolerance.

ϵ    is the RELATIVE "air gap" added to the bounds so that the bounds don't touch the function at the point of closest approach. If the function bound lies in the range [a,b] a gap of size ϵ*(b-a) will be added to the y values of all points of the upper bound and subtracted from all points of the lower bound. The default value is 1% or ϵ = 0.01
