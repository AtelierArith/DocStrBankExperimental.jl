```
affine_regions(f::Vector{Expression})
affine_regions(f::System)
```

Input a list of affine hypersurfaces 'f = [f*1,...f*k]'.  Outputs the regions in the complement of the hypersurface arrangement, their sign patterns, Euler characteristic and the indices of the critical points in each region. Accepts the same options as [`regions`](@ref).

## Example

```julia
using HypersurfaceRegions
@var x y
f = [x^2 + y^2 - 1; x^2 + y^2 - 4];
affine_regions(f)
```
