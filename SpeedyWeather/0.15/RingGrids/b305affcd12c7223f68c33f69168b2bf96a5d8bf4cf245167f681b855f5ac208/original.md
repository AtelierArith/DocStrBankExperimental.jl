An `OctaHEALPixArray` is an array of OctaHEALPix grids, subtyping `AbstractReducedGridArray`. First dimension of the underlying `N`-dimensional `data` represents the horizontal dimension, in ring order (0 to 360˚E, then north to south), other dimensions are used for the vertical and/or time or other dimensions. The resolution parameter of the horizontal grid is `nlat_half` (number of latitude rings on one hemisphere, Equator included) and the ring indices are precomputed in `rings`.

An OctaHEALPix grid has 4 faces, each `nlat_half x nlat_half` in size, covering 90˚ in longitude, pole to pole. As part of the HEALPix family of grids, the grid points are equal area. They start with 4 longitude points on the northern-most ring, increase by 4 points per ring  towards the Equator with one ring on the Equator before reducing the number of points again towards the south pole by 4 per ring. There is no equatorial belt for OctaHEALPix grids. The southern hemisphere is symmetric to the northern, mirrored around the Equator. OctaHEALPix grids have a ring on the Equator. For more details see Górski et al. 2005, DOI:10.1086/427976, the OctaHEALPix grid belongs to the family of HEALPix grids with Nθ = 1, Nφ = 4 but is not explicitly mentioned therein.

`rings` are the precomputed ring indices, for nlat_half = 3 (in contrast to HEALPix this can be odd) it is `rings = [1:4, 5:12, 13:24, 25:32, 33:36]`. For efficient looping see `eachring` and `eachgrid`. Fields are

  * `data::AbstractArray`
  * `nlat_half::Int64`
  * `rings::Vector{UnitRange{Int64}}`
