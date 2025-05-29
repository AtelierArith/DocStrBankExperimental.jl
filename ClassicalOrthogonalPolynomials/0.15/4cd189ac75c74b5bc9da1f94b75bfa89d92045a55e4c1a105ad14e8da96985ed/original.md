```
Jacobi{T}(a,b)
Jacobi(a,b)
```

The quasi-matrix representing Jacobi polynomials, where the first axes represents the interval and the second axes represents the polynomial index (starting from 1). See also [`jacobi`](@ref), [`jacobip`](@ref) and [`JacobiWeight`](@ref).

The eltype, when not specified, will be converted to a floating point data type.

# Examples

```jldoctest
julia> J=Jacobi(0, 0) # The eltype will be converted to float
Jacobi(0, 0)

julia> axes(J)
(Inclusion(-1.0 .. 1.0 (Chebyshev)), OneToInf())

julia> J[0,:] # Values of polynomials at x=0
ℵ₀-element view(::Jacobi{Float64, Int64}, 0.0, :) with eltype Float64 with indices OneToInf():
  1.0
  0.0
 -0.5
 -0.0
  0.375
  0.0
 -0.3125
 -0.0
  0.2734375
  0.0
  ⋮

julia> J0=J[:,1]; # J0 is the first Jacobi polynomial which is constant.

julia> J0[0],J0[0.5]
(1.0, 1.0)
```
