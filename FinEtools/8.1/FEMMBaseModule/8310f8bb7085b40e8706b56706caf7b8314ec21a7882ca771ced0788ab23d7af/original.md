```
integratefunction(
    self::AbstractFEMM,
    geom::NodalField{GFT},
    fh::F;
    initial::R = zero(typeof(fh(zeros(ndofs(geom), 1)))),
    m = -1,
) where {GFT<:Number, F<:Function, R<:Number}
```

Integrate a function over the discrete manifold.

Integrate some scalar function over the geometric cells. The function takes a single argument, the position vector.

When the scalar function returns just +1 (such as `(x) ->  1.0`), the result measures the volume (number of points, length, area, 3-D volume, according to the manifold dimension). When the function returns the mass density, the method measures the mass, when the function returns the x-coordinate equal measure the static moment with respect to the y- axis, and so on.

# Example:

Compute the volume of the mesh and then its center of gravity:

```
V = integratefunction(femm, geom, (x) ->  1.0, 0.0)
Sx = integratefunction(femm, geom, (x) ->  x[1], 0.0)
Sy = integratefunction(femm, geom, (x) ->  x[2], 0.0)
Sz = integratefunction(femm, geom, (x) ->  x[3], 0.0)
CG = vec([Sx Sy Sz]/V)
```

Compute a moment of inertia of the mesh relative to the origin:

```
Ixx = integratefunction(femm, geom, (x) ->  x[2]^2 + x[3]^2)
```
