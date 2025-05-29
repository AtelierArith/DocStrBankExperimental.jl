A `FullOctaHEALPixArray` is an array of full grids, subtyping `AbstractFullGridArray` that use OctaHEALPix latitudes for each ring. This type primarily equists to interpolate data from the (reduced) OctaHEALPixGrid onto a full grid for output.

First dimension of the underlying `N`-dimensional `data` represents the horizontal dimension, in ring order (0 to 360˚E, then north to south), other dimensions are used for the vertical and/or time or other dimensions. The resolution parameter of the horizontal grid is `nlat_half` (number of latitude rings on one hemisphere, Equator included) and the ring indices are precomputed in `rings`. Fields are

  * `data::AbstractArray`
  * `nlat_half::Int64`
  * `rings::Vector{UnitRange{Int64}}`
