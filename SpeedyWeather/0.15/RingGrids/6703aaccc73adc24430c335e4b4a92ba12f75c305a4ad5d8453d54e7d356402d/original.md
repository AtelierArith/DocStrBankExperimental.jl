A `HEALPixArray` is an array of HEALPix grids, subtyping `AbstractReducedGridArray`. First dimension of the underlying `N`-dimensional `data` represents the horizontal dimension, in ring order (0 to 360˚E, then north to south), other dimensions are used for the vertical and/or time or other dimensions. The resolution parameter of the horizontal grid is `nlat_half` (number of latitude rings on one hemisphere, Equator included) which has to be even (non-fatal error thrown otherwise) which is less strict than the original HEALPix formulation (only powers of two for nside = nlat_half/2). Ring indices are precomputed in `rings`.

A HEALPix grid has 12 faces, each `nside`x`nside` grid points, each covering the same area of the sphere. They start with 4 longitude points on the northern-most ring, increase by 4 points per ring in the "polar cap" (the top half of the 4 northern-most faces) but have a constant number of longitude points in the equatorial belt. The southern hemisphere is symmetric to the northern, mirrored around the Equator. HEALPix grids have a ring on the Equator. For more details see Górski et al. 2005, DOI:10.1086/427976. 

`rings` are the precomputed ring indices, for nlat_half = 4 it is `rings = [1:4, 5:12, 13:20, 21:28, 29:36, 37:44, 45:48]`. So the first ring has indices 1:4 in the unravelled first dimension, etc. For efficient looping see `eachring` and `eachgrid`. Fields are

  * `data::AbstractArray`
  * `nlat_half::Int64`
  * `rings::Vector{UnitRange{Int64}}`
