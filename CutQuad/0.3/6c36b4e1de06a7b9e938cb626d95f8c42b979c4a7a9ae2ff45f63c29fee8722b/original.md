```
wts, pts = cut_face_quad(face, dir, phi, num_quad [, fit_degree=num_quad-1])
```

Returns a quadrature for the face defined by the HyperRectangle `face` and  level-set function `phi`.  The face has a unit normal whose only non-zero component is in the direction `dir`; furthermore, if the spatial dimension is `Dim` –- which is determined by the parameter in `face` –- the HyperRectangle should have a width of zero in the direction `dir`.  The canonical quadrature on a non-cut face (i.e. `phi(x) > 0` for all `x` over `face`) uses a tensor-product Gauss-Legendre quadrature with `num_quad^(Dim-1)` points total. The `fit_degree` parameter indicates the degree of the Bernstein polynomial that the algoim library uses to represent the level-set function `phi`.  

# Example

```julia-repl
julia> using CutQuad, RegionTrees

julia> using StaticArrays: SVector

julia> phi = x-> 4*(x[1] + 1)^2 + 36*(x[2] - 0.5)^2 - 9;

julia> face = HyperRectangle(SVector{2}([0.0; 0.0]), SVector{2}([0.0; 1.0]));

julia> face_wts, face_pts = cut_face_quad(face, 1, phi, 3, fit_degree=2)
```
