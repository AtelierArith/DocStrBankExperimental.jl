```julia
relative_coordinate(
    lattice::LightLattices.RegularLattice{D, T, true, <:LightLattices.TrivialCell},
    I1::CartesianIndex{D},
    I2::CartesianIndex{D}
) -> Any

```

For periodic lattice, the "shortest" relative coordinate is calculated instead.

For, that the following heuristic is used. Cartesian indices of the two nodes are shifted by the same amount, so that the cartesian index of the second node corresponds to the central cell of the lattice. Then, the cartesian index of the first node is translated back inside the lattice. The relative coordinate is computed using the resulting indices.

This heuristic guarantees that `relative_coordinate(lattice, I1, I2) == -relative_coordinate(lattice, I2, I1)`.
