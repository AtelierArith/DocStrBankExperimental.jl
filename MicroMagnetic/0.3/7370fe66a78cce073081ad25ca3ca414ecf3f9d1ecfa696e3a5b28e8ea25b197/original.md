```
NEB(sim::AbstractSim, init_images::TupleOrArray, frames_between_images::TupleOrArray; 
    name="NEB", spring_constant=1.0e5, driver="LLG", clib_image=-1)
```

Create a NEB instance.

# Arguments

  * `sim::AbstractSim`: Simulation instance that includes the interactions.
  * `init_images::TupleOrArray`: Tuple or array of initial and final state images. Intermediate state images can also be included.
  * `frames_between_images::TupleOrArray`: Tuple or array specifying the number of frames between each pair of images.
  * `name::String="NEB"`: Name for the NEB instance.
  * `spring_constant::Float64=1.0e5`: Spring constant used in the NEB simulation.
  * `driver::String="LLG"`: Driver for the NEB simulation. Options are `"SD"` or `"LLG"`.
  * `clib_image::Int=-1`: Optional parameter for specifying a particular image in the library (default is -1).

# Returns

A NEB instance configured with the provided parameters.

# Example

```julia
# define mesh and the corresponding parameters
mesh = FDMesh(nx=60, ny=60, nz=1, dx=2e-9, dy=2e-9, dz=2e-9, pbc="xy")
params = Dict(
    :Ms => 3.84e5,
    :A => 3.25e-12,
    :D => 5.83e-4,
    :H => (0, 0, 120 * mT)
)

# Define the initial and final state, stored in the init_images list.
# Any acceptable object, such as a function, a tuple, or an array, can be used.
# The init_images list can also contain the intermediate state if you have one.
init_images = [read_vtk("skx.vts"), (0, 0, 1)]

# Define the interpolation array to specify the number of images used in the NEB simulation.
# The length of the interpolation array should be the length of init_images minus one.
# For example, if init_images = [read_vtk("skx.vts"), read_vtk("skx2.vts"), (0, 0, 1)], 
# the length of interpolation should be 2, i.e., something like interpolation = [5,5].
interpolation = [6]

# Use the create_sim method to create a Sim instance.
sim = create_sim(mesh; params...)

# Create the NEB instance and set the spring_constant. The driver can be "SD" or "LLG".
neb = NEB(sim, init_images, interpolation; name="skx_fm", driver="SD")
# neb.spring_constant = 1e7

# Relax the entire system.
relax(neb; stopping_dmdt=0.1, save_vtk_every=1000, max_steps=5000)
```
