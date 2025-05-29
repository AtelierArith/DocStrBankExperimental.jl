```
polylabel(polygon::Polygon; rtol::Real = 0.01, atol::Union{Nothing, Real} = nothing)::Tuple{Float64, Float64}
polylabel(multipoly::MultiPolygon; rtol::Real = 0.01, atol::Union{Nothing, Real} = nothing)::Tuple{Float64, Float64}
```

`polylabel` finds the pole of inaccessibility of the given polygon or multipolygon, and returns its coordinates as a 2-Tuple of `(x, y)`.  Tolerances can be specified.  

Any geometry which expresses the `GeoInterface.jl` polygon or multipolygon traits can be passed to this method, so long as it implements the `GeoInterface` methods `extent`, `contains`, and `centroid`, in addition to the polygon `coordinates`, `getexterior`, and `gethole` interfaces.

`rtol` is relative tolerance, `atol` is absolute tolerance (in the same vein as `Base.isapprox`). When `atol` is provided, it overrides `rtol`.

!!! warning
    The performance of this function is still being actively improved; specifically the signed distance function needs some optimization.  Until then, this will be much slower than the equivalent in Python/JS.

