```julia
mutable struct BinnedPointList{T}
```

Binned  point  list structure  allowing  for  fast check  for  already existing points.

This  provides better  performance for  indendifying already  inserted points than the naive linear search.

OTOH  the  implementation  is  still  quite  naive  -  it  dynamically maintains a cuboid binning region with a fixed number of bins.

Probably  tree based  adaptive  methods  (a la  octree)  will be  more efficient, however they will be harder to implement.

In an ideal world, we would maintain a dynamic Delaunay triangulation, which at  once could be  the starting  point of mesh  generation which will follow here anyway.

  * `dim::Int32`:  Space dimension

  * `tol::Any`: Point distance tolerance. Points closer than tol (in Euclidean distance) will be identified, i.e. are collapsed to the first inserted.

  * `binning_region_min::Vector`: " The union of all bins is the binning region - a cuboid given by two of its corners. It is calculated dynamically depending on the inserted points.

  * `binning_region_max::Vector`
  * `binning_region_increase_factor::Any`: Increase factor of binning region (with respect to the cuboid defined by the coordinates of the binned points)

  * `points::ElasticArrays.ElasticArray{T, 2, M, V} where {T, M, V<:DenseVector{T}}`: The actual point list

  * `bins::Array{Vector{Int32}}`: The bins are vectors of indices of points in the point list We store them in a dim-dimensional array  of length "number*of*directional_bins^dim"

  * `number_of_directional_bins::Int32`: Number of bins in each space dimension

  * `unbinned::Vector{Int32}`: Some points will fall outside of the binning region. We collect them in vector of ubinned point indices

  * `num_allowed_unbinned_points::Int32`: Number of unbinned  points tolerated without rebinning

  * `max_unbinned_ratio::Any`: Maximum ratio of unbinned  points  in point list

  * `current_bin::Vector{Int32}`: Storage of current point bin
