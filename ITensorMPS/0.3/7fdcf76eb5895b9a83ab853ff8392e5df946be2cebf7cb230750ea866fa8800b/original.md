```
square_lattice(Nx::Int,
               Ny::Int;
               kwargs...)::Lattice
```

Return a Lattice (array of LatticeBond objects) corresponding to the two-dimensional square lattice of dimensions (Nx,Ny). By default the lattice has open boundaries, but can be made periodic in the y direction by specifying the keyword argument `yperiodic=true`.
