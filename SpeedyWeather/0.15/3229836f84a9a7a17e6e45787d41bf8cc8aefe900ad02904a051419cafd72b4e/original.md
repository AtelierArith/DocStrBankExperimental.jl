Defines the horizontal spectral resolution and corresponding grid and the vertical coordinate for SpeedyWeather.jl. Options are

  * `NF::Type{<:AbstractFloat}`: [OPTION] number format used throughout the model
  * `device::SpeedyWeather.AbstractDevice`: [OPTION] device archictecture to run on
  * `ArrayType::Type{<:AbstractArray}`: [OPTION] array type to use for all variables
  * `VectorType::Type{<:AbstractVector}`: [DERIVED] Type of vector
  * `MatrixType::Type{<:AbstractMatrix}`: [DERIVED] Type of matrix
  * `TensorType::Type{<:AbstractArray}`: [DERIVED] Type of 3D array
  * `trunc::Int64`: [OPTION] horizontal resolution as the maximum degree of spherical harmonics
  * `SpectralVariable2D::Type{<:AbstractArray}`: [DERIVED] Type of spectral variable in 2D (horizontal only, flattened into 1D vector)
  * `SpectralVariable3D::Type{<:AbstractArray}`: [DERIVED] Type of spectral variable in 3D (horizontal only + e.g vertical, flattened into 2D matrix)
  * `SpectralVariable4D::Type{<:AbstractArray}`: [DERIVED] Type of spectral variable in 4D (horizontal only + e.g. vertical and time, flattened into 3D array)
  * `Grid::Type{<:SpeedyWeather.RingGrids.AbstractGrid}`: [OPTION] horizontal grid used for calculations in grid-point space
  * `GridVariable2D::Type{<:AbstractArray}`: [DERIVED] Type of grid variable in 2D (horizontal only, flattened into 1D vector)
  * `GridVariable3D::Type{<:AbstractArray}`: [DERIVED] Type of grid variable in 3D (horizontal + e.g. vertical, flattened into 2D matrix)
  * `GridVariable4D::Type{<:AbstractArray}`: [DERIVED] Type of grid variable in 4D (horizontal + e.g. vertical + time, flattened into 3D array)
  * `dealiasing::Float64`: [OPTION] how to match spectral with grid resolution: dealiasing factor, 1=linear, 2=quadratic, 3=cubic grid
  * `radius::Float64`: [OPTION] radius of the sphere [m]
  * `nparticles::Int64`: [OPTION] number of particles for particle advection [1]
  * `ParticleVector::Type{<:AbstractArray}`: [DERIVED] ArrayType of particle vector
  * `nlat_half::Int64`: [DERIVED] number of latitude rings on one hemisphere (Equator incl)
  * `nlat::Int64`: [DERIVED] number of latitude rings on both hemispheres
  * `npoints::Int64`: [DERIVED] total number of grid points in the horizontal
  * `nlayers::Int64`: [OPTION] number of vertical layers in the atmosphere
  * `nlayers_soil::Int64`: [OPTION] number of vertical layers in the soil/land

`nlat_half` and `npoints` should not be chosen but are derived from `trunc`, `Grid` and `dealiasing`.
