```
DerivativeMap(m::ConformalMap)
```

Constructs new conformal maps from the first and second derivatives of the conformal map `m`.

These new conformal maps can be evaluated at a single or vector of points just as  `m` is. The first entry in the tuple returned is the first derivative, the second entry is the second derivative.

# Example

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p);

julia> dm = DerivativeMap(m);

julia> ζ = [0.1,0.5-0.75im,-0.25-0.3im];

julia> dz, ddz = dm(ζ;inside=true);

julia> dz
3-element Array{Complex{Float64},1}:
  67.2068+76.6284im
 -1.11666+0.544576im
  3.99129-5.30641im
```
