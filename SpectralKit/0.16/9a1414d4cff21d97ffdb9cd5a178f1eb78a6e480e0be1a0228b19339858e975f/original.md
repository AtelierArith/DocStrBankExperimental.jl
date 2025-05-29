```julia
coordinate_transformations(transformations)

```

Wrapper for coordinate-wise transformations. To extract components, convert to Tuple.

```jldoctest
julia> using StaticArrays

julia> ct = coordinate_transformations(BoundedLinear(0, 2), SemiInfRational(2, 3))
coordinate transformations
  (0.0,2.0) ↔ domain [linear transformation]
  (2,∞) ↔ domain [rational transformation with scale 3]

julia> d1 = domain(Chebyshev(InteriorGrid(), 5))
[-1,1]

julia> dom = coordinate_domains(d1, d1)
[-1,1]²

julia> x = transform_from(dom, ct, (0.4, 0.5))
(1.4, 11.0)

julia> y = transform_to(dom, ct, x)
(0.3999999999999999, 0.5)
```
