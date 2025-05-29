```
InverseMap(m::ConformalMap)
```

Constructs the inverse conformal map of the conformal map `m`.

This inverse conformal map can be evaluated at a single or vector of points. Points should be outside the body. Whether the resulting point in the circle plane is interpreted inside or outside the circle is determined by the optional argument `inside`, which defaults to `false`.

# Example

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p);

julia> m⁻¹ = InverseMap(m);

julia> ζ = [1.0+3.0im,-2.0-2.0im,0.1+1.1im];

julia> m⁻¹(m(ζ))
3-element Array{Complex{Float64},1}:
  1.0+3.0im
 -2.0-2.0im
  0.1+1.1im
```
