```
wts, pts = cut_cell_quad(cell, phi, num_quad [, fit_degree=num_quad-1])
```

Returns a volume quadrature for the domain defined by the HyperRectangle `cell`  and level-set function `phi`.  The canonical quadrature on a non-cut domain (i.e. `phi(x) > 0` for all `x`) uses a tensor-product Gauss-Legendre quadrature  with `num_quad^Dim` points total, where `Dim` is the dimension of the domain. The `fit_degree` parameter indicates the degree of the Bernstein polynomial that the algoim library uses to represent the level-set function `phi`.  

# Example

```julia-repl
julia> using CutQuad, RegionTrees

julia> using StaticArrays: SVector

julia> phi = x-> 4*(x[1] + 1)^2 + 36*(x[2] - 0.5)^2 - 9;

julia> cell = HyperRectangle(SVector{2}([0.0; 0.0]), SVector{2}([1.0; 1.0]));

julia> wts, pts = cut_cell_quad(cell, phi, 3, fit_degree=2)
```
