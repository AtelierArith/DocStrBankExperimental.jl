```
i = rays(rg::SinoGeom)
```

Radial `r` and angular `ϕ` coordinates (in radians) of all sinogram elements for the given geometry. Return type of `i` is a `ProductIterator` that makes tuples of the form `(r, ϕ)`. To make projections call `p = [fun(c...) for c in i]` where `fun` is `radon(...)`.
