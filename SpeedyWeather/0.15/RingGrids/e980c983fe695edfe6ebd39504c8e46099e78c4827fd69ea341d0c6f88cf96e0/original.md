A `FullGaussianArray` is an array of full grids, subtyping `AbstractFullGridArray`, that use Gaussian latitudes for each ring. First dimension of the underlying `N`-dimensional `data` represents the horizontal dimension, in ring order (0 to 360˚E, then north to south), other dimensions are used for the vertical and/or time or other dimensions. The resolution parameter of the horizontal grid is `nlat_half` (number of latitude rings on one hemisphere, Equator included) and the ring indices are precomputed in `rings`. Fields are

  * `data::AbstractArray`: Data array, west to east, ring by ring, north to south.
  * `nlat_half::Int64`: Number of latitudes on one hemisphere
  * `rings::Vector{UnitRange{Int64}}`: Precomputed ring indices, ranging from first to last grid point on every ring.
