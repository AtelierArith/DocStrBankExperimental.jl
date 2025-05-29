```
localanisotropies(Geometric, searcher; simplify=true)
```

Extract `LocalAnisotropy` from a searcher object. Based on the spatial data and the parameters from the searcher object, a group of neighbor points is collected at each place. PCA is applied to their spatial coordinates, returning eigenvectors that represent a local ellipse/ellipsoid aligned with the directions with more clustered points. The magnitude is the ratio of the PCA eigenvalues. It's useful to extract local anisotropies from 3-D surface points. If `simplify = true` and data is 3-D, only the minimum direction is extracted from PCA; the other axes are calculated (main direction will be always along max dip direction and the intermediate axis will be orthogonal to the others). This is default for 3-D.

## Example

```julia
searcher = KNearestSearch(pts3dsurface, 10)
prelpars = localanisotropies(Geometric, searcher) # extract local pars at surface
lpars = idwpars(prelpars, searcher, grid) # interpolate local pars to a grid
```
