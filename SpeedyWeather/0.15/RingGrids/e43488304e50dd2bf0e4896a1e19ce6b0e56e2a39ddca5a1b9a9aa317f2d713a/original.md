A `FullClenshawArray` is an array of full grid, subtyping `AbstractFullGridArray`, that use equidistant latitudes for each ring (a regular lon-lat grid). These require the Clenshaw-Curtis quadrature in the spectral transform, hence the name. One ring is on the equator, total number of rings is odd, no rings on the north or south pole. First dimension of the underlying `N`-dimensional `data` represents the horizontal dimension, in ring order (0 to 360˚E, then north to south), other dimensions are used for the vertical and/or time or other dimensions. The resolution parameter of the horizontal grid is `nlat_half` (number of latitude rings on one hemisphere, Equator included) and the ring indices are precomputed in `rings`. Fields are

  * `data::AbstractArray`
  * `nlat_half::Int64`
  * `rings::Vector{UnitRange{Int64}}`
