```
abstract type AbstractUniformMesh{T,DIM} <: AbstractMesh{T,DIM}
```

Parent type of all uniform meshes. 

Mesh points of a uniform mesh is assumed to be uniformly distributed  in an parrallelogram area. Uniform meshes support fractional coordinates.

All concrete implementations of this abstract type are assumed to have the following fields:

# Required Fields:

  * `origin`: the origin(bottom-left point) of the area
  * `shift`: the fractional coordinate shift of the mesh. This is useful to reproduce M-P mesh commonly used in DFT.

and have the following methods implemented:

# Required Methods:

  * `lattice_vector`: return lattice vector of the represented area
  * `inv_lattice_vector`: return inverse of lattice vector
  * `cell_volume`: return cell volume
