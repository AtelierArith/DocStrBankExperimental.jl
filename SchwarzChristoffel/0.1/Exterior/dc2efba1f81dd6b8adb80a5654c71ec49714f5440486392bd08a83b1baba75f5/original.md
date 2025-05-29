```
summary(m::ConformalMap)
```

Returns a summary of data for a conformal map

# Example

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p);

julia> summary(m)
Schwarz-Christoffel map of unit circle to exterior of polygon with 4 vertices
   vertices: (-1.0,-1.0), (0.2,-1.0), (1.0,0.5), (-1.0,1.0),
   interior angles/π: 0.5, 0.656, 0.422, 0.422,
   prevertices on circle: (1.0,0.0), (0.3764,-0.9265), (-0.9024,-0.4309), (-0.1868,0.9824),
   prevertex angles/π: -0.7291, -0.3519, 0.1291, 0.7111,
   constant = 0.6722 + 0.7669im, accuracy = 1.0e-8,
   number of multipole coefficients = 100
```
