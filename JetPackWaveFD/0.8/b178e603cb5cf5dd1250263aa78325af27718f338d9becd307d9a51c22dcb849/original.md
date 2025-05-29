```
g = Ginsu(r0, dr, nr, sour, recr, padr, ndamp; dims=(:z,:y,:x), stencilhalfwidth=2, vector_width=8)
```

Create a Ginsu object that defines the model aperture for a given shot.  `g` is used to subset earth  models using the `sub` and `sub!` methods, and provides the inverse operation using the `super`,  `super!` and `super_accumulate!` methods.  The padding for the earth model subset is determined  from the source and receiver positions, along with the padding `padr` and damping region `ndamp`  parameters.

# required parameters[1,2]

  * `r0::NTuple{N,Real}` model origin in each model dimension
  * `dr::NTuple{N,Real}` model cell widths in each model dimension
  * `nr::NTuple{N,Int}` model cell counts in each model dimension
  * `sour::NTuple{N,Vector{Float}}` source locations in each model dimension
  * `recr::NTuple{N,Vector{Float}}` receiver locations in each model dimension
  * `padr::NTuple{N,NTuple{Real,Real}}` padding beyond the survey aperture in each model dimension[3,4]
  * `ndamp::NTuple{N,NTuple{Int,Int}}` damping region for absorbing boundaies in each model dimension[3,4]

# named optional parameters

  * `dim=(:z,:y,:x)` axis ordering with the default being `z` fast, and `x` slow
  * `stencilhalfwidth=0` if there is a free-surface, set `stencilhalfwidth`, padr, and ndamp accordingly. This will add `stencilhalfwidth` cells above the free surface to allow copying the mirrored model to implement the free surface boundary condition.
  * `vector_width=8` sets the width required for vectorization of the code, and ensures that the size(ginsu) divided by vector_width has remainder zero for each dimension.

# type specification

  * `g.lextrng` is the logical (1-based) indices for the Ginsu model subset
  * `g.lintrng` is the logical (1-based) indices for the Ginsu model subset interior
  * `rₒ` is the physical origin of the Ginsu model subset
  * `δr` is the grid cell sizes

# Notes

1. `N` is the number of model dimensions
2. `rₒ[i]` is the model origin along the ith model dimension
3. the model padding is the combination of `padr` and `ndamp`
4. `padr[i][1]` is the padding for the dimension start, and `padr[i][2]` for the end.  The same is true for `ndamp`.

## Example (free-surface)

```
o---------------c---x--------------x---c-------o
|               |   |              |   |       |
|               |   |              |   |       |
|               |   |              |   |       |
|               |   |              |   |       |
|               |   x--------------x   |       |
|               |                      |       |
o---------------c----------------------c-------o
```

  * `o` denotes the original model
  * `c` denotes the Ginsu module subset
  * `x` denotes the Ginsu model subset interior
  * the region falling in-between the Ginsu model subset and the Ginsu model subset interior is the absorbing boundary region.
