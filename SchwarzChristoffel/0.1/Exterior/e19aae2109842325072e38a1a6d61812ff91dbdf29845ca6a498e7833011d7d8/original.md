```
PowerMap(c::Vector{ComplexF64}[;N = 200]) <: ConformalMap
```

Create a power series map from the exterior of the unit circle to the exterior of a shape defined by the power series coefficients `c`.

The form of the mapping is

$$
z(\zeta) = c_{1}\zeta + c_{0} + \sum_{j=1}^{N_{c}} \frac{c_{-j}}{\zeta^{j}}
$$

The entries in `c` correspond as follows: `c[1]` $\rightarrow c_{1}$, `c[2]` $\rightarrow c_{0}$, `c[3]` $\rightarrow c_{-1}$, etc.

The resulting map `m` can be evaluated at a single or a vector of points `ζ` with `m(ζ)`.

# Example

```jldoctest
julia> c = ComplexF64[1,0,1/4];

julia> m = PowerMap(c)
Power series map

julia> ζ = [1.0+3.0im,-2.0-2.0im,0.0+1.1im];

julia> m(ζ)
3-element Array{Complex{Float64},1}:
   1.025+2.925im
 -2.0625-1.9375im
     0.0+0.872727im
```
