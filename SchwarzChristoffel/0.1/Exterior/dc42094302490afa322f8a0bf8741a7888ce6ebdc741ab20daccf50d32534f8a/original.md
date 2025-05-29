```
ExteriorMap(p::Polygon[;tol::Float64][,ncoeff::Int]) <: ConformalMap
```

Create a Schwarz-Christoffel map from the interior or exterior of the unit circle to the exterior of polygon `p`.

# Example

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p)
Schwarz-Christoffel map of unit circle to exterior of polygon with 4 vertices
```

`ExteriorMap(p;tol=1e-12)` manually sets the tolerance to `1e-12` (the default is 1e-8).

`ExteriorMap(p;ncoeff=200)` manually sets the number of coefficients of negative powers of the multipole expansion of the mapping to `200` (the default is 100).

The resulting map `m` can be evaluated at a single or vector of points `ζ` with `m(ζ[;inside::Bool])`. The points are assumed to lie outside the unit circle, unless the optional argument `inside=true`, in which case they are assumed to lie inside the circle.

# Example

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p);

julia> ζ = [0.1,0.5-0.75im,-0.25-0.3im];

julia> m(ζ;inside=true)
3-element Array{Complex{Float64},1}:
   -6.9344-7.68965im
 0.0439774-1.11249im
   2.41181-0.044779im

julia> ζ = [1.0+3.0im,-2.0-2.0im,0.0+1.1im];

julia> m(ζ)
3-element Array{Complex{Float64},1}:
   0.81614+3.02956im
  -2.25237-2.08523im
 -0.333104+0.975837im
```
