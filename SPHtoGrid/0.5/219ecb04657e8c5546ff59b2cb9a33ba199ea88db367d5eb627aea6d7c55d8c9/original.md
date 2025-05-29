```
mass_density(pos::Matrix{<:Real}, mass::Vector{<:Real}; 
             kernel::AbstractSPHKernel=Cubic(Float64, 3),
             Nneighbors::Integer=32,
             boxsize::Vector{<:Real}=zeros(3),
             verbose::Bool=false)
```

Compute the density of an arbitrary particle distribution using the SPH method. Neighbor searches are performed using a (periodic) BallTree. The density is computed in input units, so additional unit conversion to cgs units is required, if input units are not cgs.

## Arguments:

  * `pos`: particle position in physical code units.
  * `mass`: particle mass in physical code units.

## Keyword Arguments

  * `kernel::AbstractSPHKernel=Cubic(Float64, 3)`: SPH kernel to use for the density estimate. Works with any kernel from [SPHKernels.jl](https://github.com/LudwigBoess/SPHKernels.jl).
  * `Nneighbors::Integer=32`: Number of neighboring particles to use for the density estimate.
  * `boxsize::Vector{<:Real}=zeros(3)`: Boxsize in each dimension. Used for periodic boundary conditions. If set to zero, non-periodic boundary conditions are assumed.
  * `verbose::Bool=false`: If set to true gives progress reports and progress bar.

## Returns

  * `rho`:  mass density at particle position in input units.
  * `hsml`: smoothing length of each particle in input units.

## Mapping settings

  * weight function: [`part_weight_physical`](@ref)
  * reduce image: `false`
