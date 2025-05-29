```
Body(material, position, volume)
Body(material, inp_file)
```

Construct a `Body` for a peridynamics simulation.

# Arguments

  * `material::AbstractMaterial`: The material which is defined for the whole body.   Available material models:

      * [`BBMaterial`](@ref): Bond-based peridynamics
      * [`OSBMaterial`](@ref): Ordinary state-based peridynamics
      * [`CMaterial`](@ref): Correspondence formulation
      * [`BACMaterial`](@ref): Bond-associated correspondence formulation of Chen and Spencer
      * [`CKIMaterial`](@ref): Continuum-kinematics-inspired peridynamics
  * `position::AbstractMatrix`: A `3×n` matrix with the point position of the `n` points.
  * `volume::AbstractVector`: A vector with the volume of each point.
  * `inp_file::AbstractString`: An Abaqus input file containing meshes, imported with   [`read_inp`](@ref).

# Throws

  * Error if the number of points is not larger than zero.
  * Error if `position` is not a `3×n` matrix and has the same length as `volume`.
  * Error if `position` or `volume` contain `NaN` values.

# Example

```julia-repl
julia> Body(BBMaterial(), rand(3, 10), rand(10))
10-point Body{BBMaterial{NoCorrection}}:
  1 point set(s):
    10-point set `all_points`
```

---

!!! warning "Internal use only"
    Please note that the fields are intended for internal use only. They are *not* part of the public API of Peridynamics.jl, and thus can be altered (or removed) at any time without it being considered a breaking change.


```julia
Body{Material,PointParameters}
```

# Type Parameters

  * `Material <: AbstractMaterial`: Type of the specified material model.
  * `PointParameters <: AbstractPointParameters`: Type of the point parameters.

# Fields

  * `mat::Material`: The material formulation.
  * `n_points::Int`: The number of points that in the body.
  * `position::Matrix{Float64}`: A `3×n_points` matrix with the position of the points.
  * `volume::Vector{Float64}`: A vector with the volume of each point.
  * `fail_permit::Vector{Bool}`: A vector that describes if failure is allowed for each point.
  * `point_sets::Dict{Symbol,Vector{Int}}`: A dictionary containing point sets.
  * `point_params::Vector{PointParameters}`: A vector containing all different point parameter   instances of the body. Each point can have its own `PointParameters` instance.
  * `params_map::Vector{Int}`: A vector that maps each point index to a parameter instance in   `point_params`.
  * `single_dim_bcs::Vector{SingleDimBC}`: A vector with boundary conditions on a single   dimension.
  * `posdep_single_dim_bcs::Vector{PosDepSingleDimBC}`: A vector with position dependent   boundary conditions on a single dimension.
  * `single_dim_ics::Vector{SingleDimIC}`: A vector with initial conditions on a single   dimension.
  * `posdep_single_dim_ics::Vector{PosDepSingleDimIC}`: A vector with position dependent   initial conditions on a single dimension.
  * `data_bcs::Vector{DataBC}`: A vector with data boundary conditions.
  * `point_sets_precracks::Vector{PointSetsPreCrack}`: A vector with predefined point set   cracks.
