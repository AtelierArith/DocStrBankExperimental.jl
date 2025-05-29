```
trixi2vtk(vu_ode, semi, t; iter=nothing, output_directory="out", prefix="",
          write_meta_data=true, max_coordinates=Inf, custom_quantities...)
```

Convert Trixi simulation data to VTK format.

# Arguments

  * `vu_ode`: Solution of the TrixiParticles ODE system at one time step.           This expects an `ArrayPartition` as returned in the examples as `sol.u[end]`.
  * `semi`:   Semidiscretization of the TrixiParticles simulation.
  * `t`:      Current time of the simulation.

# Keywords

  * `iter=nothing`:           Iteration number when multiple iterations are to be stored in                           separate files. This number is just appended to the filename.
  * `output_directory="out"`: Output directory path.
  * `prefix=""`:              Prefix for output files.
  * `write_meta_data=true`:   Write meta data.
  * `max_coordinates=Inf`     The coordinates of particles will be clipped if their absolute                           values exceed this threshold.
  * `custom_quantities...`:   Additional custom quantities to include in the VTK output.                           Each custom quantity must be a function of `(system, data, t)`,                           which will be called for every system, where `data` is a named                           tuple with fields depending on the system type, and `t` is the                           current simulation time. Check the available data for each                           system with `available_data(system)`.                           See [Custom Quantities](@ref custom_quantities)                           for a list of pre-defined custom quantities that can be used here.

# Example

```jldoctest; output = false, setup = :(trixi_include(@__MODULE__, joinpath(examples_dir(), "fluid", "hydrostatic_water_column_2d.jl"), tspan=(0.0, 0.01), callbacks=nothing))
trixi2vtk(sol.u[end], semi, 0.0, iter=1, output_directory="output", prefix="solution")

# Additionally store the kinetic energy of each system as "my_custom_quantity"
trixi2vtk(sol.u[end], semi, 0.0, iter=1, my_custom_quantity=kinetic_energy)

# output

```
