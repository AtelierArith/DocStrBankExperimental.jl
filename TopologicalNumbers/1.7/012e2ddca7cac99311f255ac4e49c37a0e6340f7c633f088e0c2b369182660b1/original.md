```
calcChernSurface(H::Function, kn::String; kn_mesh::Int=51, N::Int=51, gapless::Real=0.0, rounds::Bool=true, plot::Bool=false)
```

Arguments

  * Hamiltionian::Function: The Hamiltonian matrix with three-dimensional wavenumber `k` as an argument.
  * kn::String: Compute the Chern number of the plane perpendicular to the `"kn"` direction in Brillouin zone (`"k1"`, `"k2"`, `"k3"`).
  * kn_mesh::T: Number of mesh in `"kn"` direction.
  * N::Int=51: The number of meshes when discretizing the Brillouin Zone. It is preferable for `N` to be an odd number to increase the accuracy of the calculation.
  * gapless::Real: The threshold that determines the state to be degenerate. Coarsening the mesh(`N`) but increasing `gapless` will increase the accuracy of the calculation.
  * rounds::Bool=true: An option to round the value of the topological number to an integer value. The topological number returns a value of type `Int` when `true`, and a value of type `Float` when `false`.
