```julia
struct RegularLattice{D, T, PB, CT, L<:Union{Nothing, Symbol}} <: LightLattices.AbstractLattice{D, T, PB}
```

  * `lattice_dims::NTuple{D, Int64} where D`: The number of basis cells along each of the basis directions.

  * `basis::StaticArraysCore.SMatrix{D, D} where D`: Coordinates of the basis vectors of the underlying Bravais lattice. `basis[:, i]` gives the $i$-th basis vector.

  * `unit_cell::Any`: Unit cell of the lattice.

  * `label::Union{Nothing, Symbol}`: Label of the Lattice.

  * `num_of_cells::Int64`: Total number of cells.

  * `num_of_nodes::Int64`: Total number of nodes.

  * `central_cell::CartesianIndex`: Cartesian index of the central cell (in the case of even length among of dimensions it is an approximation).

This type describes a regular arrangment of nodes in `D`-dimensional space with boundary condition `PB` (`PB=true` for periodic boundary conditions, `PB=false` for free periodic boundary conditions). A general lattice consists of identicall cells (combinations of nodes) arranged as a Bravais lattice.
