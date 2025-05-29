```
Legendre{T=Float64}(a,b)
```

The quasi-matrix representing Legendre polynomials, where the first axes represents the interval and the second axes represents the polynomial index (starting from 1). See also [`legendre`](@ref), [`legendrep`](@ref), [`LegendreWeight`](@ref) and [`Jacobi`](@ref).

# Examples

```jldoctest
julia> P = Legendre()
Legendre()

julia> typeof(P) # default eltype
Legendre{Float64}

julia> axes(P)
(Inclusion(-1.0 .. 1.0 (Chebyshev)), OneToInf())

julia> P[0,:] # Values of polynomials at x=0
ℵ₀-element view(::Legendre{Float64}, 0.0, :) with eltype Float64 with indices OneToInf():
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

julia> P₀=P[:,1]; # P₀ is the first Legendre polynomial which is constant.

julia> P₀[0],P₀[0.5]
(1.0, 1.0)
```
