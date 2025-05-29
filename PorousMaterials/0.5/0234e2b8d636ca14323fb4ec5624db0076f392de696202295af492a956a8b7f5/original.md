Data structure for a regular [equal spacing between points in each coordinate] grid of points superimposed on a unit cell box (`Box`). Each grid point has data, `data`, associated with it, of type `T`, stored in a 3D array.

# Attributes

  * `box::Box`: describes Bravais lattice over which a grid of points is super-imposed. grid points on all faces are included.
  * `n_pts::Tuple{Int, Int, Int}`: number of grid points in x, y, z directions. 0 and 1 fractional coordinates are included.
  * `data::Array{T, 3}`: three dimensional array conaining data associated with each grid point.
  * `units::Symbol`: the units associated with each data point.
  * `origin::Array{Float64, 1}`: the origin of the grid.
