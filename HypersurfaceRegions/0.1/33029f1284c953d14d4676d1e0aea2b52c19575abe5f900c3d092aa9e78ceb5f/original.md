```
projective_regions(C::RegionsResult)
```

Returns a vector of vectors. The entries of the vectors are those regions in `C`, which are fused in projective space.

The following code will return a vector of vectors of type `Region`:

```julia
using HypersurfaceRegions
@var x y
f = [x^2 + y^2 - 1; x^2 + y^2 - 4];
C = regions(f)
p = projective_regions(C)
```
